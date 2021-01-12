---
title: Azure Bot Service と LUIS との統合
description: このコースを完了すると、HoloLens 2 アプリケーション内に Azure Bot Service と自然言語の理解を実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, Hololens 2, Azure Bot Service, LUIS, 自然言語, 会話ボット, Azure クラウド サービス, Azure Custom Vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 70d136467bc677c028614429e6e197ce25b30327
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008252"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="49910-104">5.Azure Bot Service の統合</span><span class="sxs-lookup"><span data-stu-id="49910-104">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="49910-105">このチュートリアルでは、**HoloLens 2** デモ アプリケーションの **Azure Bot Service** を使用して Language Understanding (LUIS) を追加し、ユーザーが **追跡対象オブジェクト** を検索するときにボットで支援できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49910-105">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="49910-106">これは 2 部構成のチュートリアルです。第 1 部では [Bot Composer](https://docs.microsoft.com/composer/introduction) を使用して、コード不要のソリューションとしてボットを作成します。また、必要なデータをボットにフィードする Azure 関数を簡単に確認します。</span><span class="sxs-lookup"><span data-stu-id="49910-106">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](https://docs.microsoft.com/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="49910-107">第 2 部では、Unity プロジェクトの **BotManager (スクリプト)** を使用して、ホストされた Bot Service を使用します。</span><span class="sxs-lookup"><span data-stu-id="49910-107">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="49910-108">目標</span><span class="sxs-lookup"><span data-stu-id="49910-108">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="49910-109">第 1 部</span><span class="sxs-lookup"><span data-stu-id="49910-109">Part 1</span></span>

* <span data-ttu-id="49910-110">Azure Bot Service の基本について学習する</span><span class="sxs-lookup"><span data-stu-id="49910-110">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="49910-111">Bot Composer を使用してボットを作成する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="49910-111">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="49910-112">Azure 関数を使用して Azure ストレージからデータを提供する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="49910-112">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="49910-113">第 2 部</span><span class="sxs-lookup"><span data-stu-id="49910-113">Part 2</span></span>

* <span data-ttu-id="49910-114">このプロジェクトで Azure Bot Service を使用するシーンをセットアップする方法を学習する</span><span class="sxs-lookup"><span data-stu-id="49910-114">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="49910-115">ボットとの会話によってオブジェクトを設定および検索する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="49910-115">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="49910-116">Azure Bot Service について</span><span class="sxs-lookup"><span data-stu-id="49910-116">Understanding Azure Bot Service</span></span>

<span data-ttu-id="49910-117">**Azure Bot Service** によって開発者は、**LUIS** を利用してユーザーとの自然な会話を維持できるインテリジェントなボットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="49910-117">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="49910-118">会話ボットは、ユーザーがどのようにアプリケーションと対話できるかを拡張する優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="49910-118">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="49910-119">ボットは、[Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) の優れた機能によって高度な会話を維持する、[QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) を使用したナレッジ ベースとして機能することができます。</span><span class="sxs-lookup"><span data-stu-id="49910-119">A Bot can act as a knowledge base with a [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span></span>

<span data-ttu-id="49910-120">[Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true) の詳細情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49910-120">Learn more about [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="49910-121">第 1 部 - ボットを作成する</span><span class="sxs-lookup"><span data-stu-id="49910-121">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="49910-122">Unity アプリケーションでボットを使用するには、まずそれを開発し、データを提供して、**Azure** 上でホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="49910-122">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="49910-123">ボットの目的は、データベースに格納されている "*追跡対象オブジェクト*" の数を確認し、"*追跡対象オブジェクト*" をその名前で検索して、それに関する基本的な情報をユーザーに通知できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="49910-123">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="49910-124">追跡対象オブジェクトの Azure 関数の概要</span><span class="sxs-lookup"><span data-stu-id="49910-124">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="49910-125">これからボットの作成を開始しますが、それを有効にするには、データをプルできるリソースを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49910-125">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="49910-126">"*ボット*" によって **追跡対象オブジェクト** の量をカウントしたり、名前で特定のものを検索して詳細を示したりできるため、**Azure テーブル ストレージ** にアクセスできるシンプルな Azure 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="49910-126">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="49910-127">追跡対象オブジェクトの Azure 関数プロジェクトをダウンロードし ([AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip))、それをハード ドライブに抽出します。</span><span class="sxs-lookup"><span data-stu-id="49910-127">Download the Tracked Objects Azure Function project: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="49910-128">この Azure 関数には、**Count** と **Find** という 2 つのアクションがあり、基本的な *HTTP* *GET* 呼び出しを使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="49910-128">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="49910-129">**Visual Studio** でコードを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="49910-129">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="49910-130">[Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview) の詳細情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49910-130">Learn more about [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="49910-131">**Count** 関数では、非常にシンプルに、テーブルにあるすべての **TrackedObjects** のクエリを **Table Storage** に実行します。</span><span class="sxs-lookup"><span data-stu-id="49910-131">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="49910-132">一方、**Find** 関数では、*GET* 要求から *name* クエリ パラメーターを受け取り、一致する **TrackedObject** のクエリを **テーブル ストレージ** に対して実行し、DTO を JSON として返します。</span><span class="sxs-lookup"><span data-stu-id="49910-132">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="49910-133">この **Azure 関数** を **Visual Studio** から直接デプロイできます。</span><span class="sxs-lookup"><span data-stu-id="49910-133">You can deploy this **Azure Function** directly from **Visual Studio**.</span></span>
<span data-ttu-id="49910-134">Azure 関数のデプロイについては、[こちら](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml&preserve-view=true)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49910-134">Find here all information regarding [Azure Function deployment](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml&preserve-view=true).</span></span>

<span data-ttu-id="49910-135">デプロイが完了したら、対応するリソースを **Azure Portal** で開き、 *[設定]* セクションの下にある **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49910-135">Once you have completed the deployment, in the **Azure Portal**, open the corresponding resource and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="49910-136">**[アプリケーション設定]** で、**追跡対象オブジェクト** が格納されている **Azure ストレージ** への "*接続文字列*" を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49910-136">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="49910-137">**[新しいアプリケーション設定]** をクリックし、名前として **AzureStorageConnectionString** を使用し、値として正しい "*接続文字列*" を指定します。</span><span class="sxs-lookup"><span data-stu-id="49910-137">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="49910-138">その後、 **[保存]** をクリックすると、**Azure 関数** の準備が完了し、次に作成する "*ボット*" にサービスを提供できるようになります。</span><span class="sxs-lookup"><span data-stu-id="49910-138">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="49910-139">会話ボットの作成</span><span class="sxs-lookup"><span data-stu-id="49910-139">Creating a conversation Bot</span></span>

<span data-ttu-id="49910-140">Bot Framework ベースの会話ボットを開発するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="49910-140">There are several ways to develope a Bot Framework based conversational bot.</span></span> <span data-ttu-id="49910-141">このレッスンでは、[Bot Framework Composer](https://docs.microsoft.com/composer/) デスクトップ アプリケーションを使用します。これは、迅速な開発に最適なビジュアル デザイナーです。</span><span class="sxs-lookup"><span data-stu-id="49910-141">In this lesson you will use the [Bot Framework Composer](https://docs.microsoft.com/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="49910-142">最新リリースは、[GitHub リポジトリ](https://github.com/microsoft/BotFramework-Composer/releases)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="49910-142">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="49910-143">Windows、Mac、Linux で使用できます。</span><span class="sxs-lookup"><span data-stu-id="49910-143">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="49910-144">**Bot Framework Composer** のインストール完了後、アプリケーションを開始すると、次のインターフェイスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="49910-144">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![Bot Framework Composer ホーム](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="49910-146">このチュートリアルに必要なダイアログとトリガーが提供されるボット コンポーザー プロジェクトを準備してあります。</span><span class="sxs-lookup"><span data-stu-id="49910-146">We have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span> <span data-ttu-id="49910-147">Bot Framework Composer プロジェクトをダウンロードし ([BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip))、それをハード ドライブに抽出します。</span><span class="sxs-lookup"><span data-stu-id="49910-147">Download the Bot Framework Composer project: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="49910-148">上部のバーで **[開く]** をクリックし、ダウンロードした Bot Framework プロジェクトを選択します。それには **TrackedObjectsBot** という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="49910-148">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="49910-149">プロジェクトが完全に読み込まれると、プロジェクトの準備ができていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="49910-149">After the project is fully loaded, you should see the project ready.</span></span>

![TrackedObjectsBot プロジェクトが開かれている Bot Framework Composer](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="49910-151">左側にフォーカスを移動して、**ダイアログ パネル** を確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="49910-151">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="49910-152">**TrackedObjectsBot** という名前のダイアログが 1 つあります。その下に、いくつかの **トリガー** を確認できます。</span><span class="sxs-lookup"><span data-stu-id="49910-152">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="49910-153">[Bot Framework の概念](https://docs.microsoft.com/composer/concept-dialog)についての詳細情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49910-153">Learn more about [Bot Framework concepts](https://docs.microsoft.com/composer/concept-dialog).</span></span>

<span data-ttu-id="49910-154">これらのトリガーで以下のことを実行します。</span><span class="sxs-lookup"><span data-stu-id="49910-154">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="49910-155">Greeting</span><span class="sxs-lookup"><span data-stu-id="49910-155">Greeting</span></span>

<span data-ttu-id="49910-156">これは、"*ユーザー*" が会話を開始したときの、チャット "*ボット*" のエントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="49910-156">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![TrackedObjectsBot プロジェクト ダイアログのトリガー Greeting](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="49910-158">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="49910-158">AskingForCount</span></span>

<span data-ttu-id="49910-159">このダイアログは、"*ユーザー*" がすべての **追跡対象オブジェクト** をカウントすることを要求したときにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="49910-159">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="49910-160">トリガー フレーズは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="49910-160">These are the trigger phrases:</span></span>

>* <span data-ttu-id="49910-161">count me all (すべてカウント)</span><span class="sxs-lookup"><span data-stu-id="49910-161">count me all</span></span>
>* <span data-ttu-id="49910-162">how many are stored (何個格納されている)</span><span class="sxs-lookup"><span data-stu-id="49910-162">how many are stored</span></span>

![TrackedObjectsBot プロジェクト ダイアログのトリガー AskForCount](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="49910-164">[LUIS](https://docs.microsoft.com/composer/how-to-use-luis) を活用することで、"*ユーザー*" はそのように厳密なフレーズでたずねる必要がなく、"*ユーザー*" にとって自然な会話ができます。</span><span class="sxs-lookup"><span data-stu-id="49910-164">Thanks to [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="49910-165">このダイアログでは、"*ボット*" から Azure 関数 **Count** への会話も行われます。それについては後で詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="49910-165">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="49910-166">Unknown Intent</span><span class="sxs-lookup"><span data-stu-id="49910-166">Unknown Intent</span></span>

<span data-ttu-id="49910-167">このダイアログは、"*ユーザー*" からの入力が、他のどのトリガー条件にも適合しない場合にトリガーされ、ユーザーに再度質問を試みる応答を行います。</span><span class="sxs-lookup"><span data-stu-id="49910-167">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![TrackedObjectsBot プロジェクト ダイアログのトリガー Unknown Intent](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="49910-169">FindEntity</span><span class="sxs-lookup"><span data-stu-id="49910-169">FindEntity</span></span>

<span data-ttu-id="49910-170">最後のダイアログは、データを分岐して "*ボット*" メモリに格納することで、より複雑になります。</span><span class="sxs-lookup"><span data-stu-id="49910-170">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="49910-171">詳細情報を知る必要がある **追跡対象オブジェクト** の *name* をユーザーにたずね、Azure 関数 **Find** に対してクエリを実行し、その応答を使用して会話を続行します。</span><span class="sxs-lookup"><span data-stu-id="49910-171">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![TrackedObjectsBot プロジェクト ダイアログのトリガー FindEntity](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="49910-173">**追跡対象オブジェクト** が見つからない場合は、ユーザーに通知し、会話を終了します。</span><span class="sxs-lookup"><span data-stu-id="49910-173">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="49910-174">該当する **追跡対象オブジェクト** が見つかった場合は、ボットによって、使用可能なプロパティが何であるかが確認され、それらについて報告が行われます。</span><span class="sxs-lookup"><span data-stu-id="49910-174">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="49910-175">ボットの適応</span><span class="sxs-lookup"><span data-stu-id="49910-175">Adapting the Bot</span></span>

<span data-ttu-id="49910-176">**AskingForCount** および **FindEntity** トリガーからバックエンドへの会話が必要です。これは、さきほどデプロイした **Azure 関数** の正しい URL を追加する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="49910-176">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="49910-177">ダイアログ パネルで **[AskingForCount]** をクリックし、 *[HTTP 要求を送信します]* というアクションを見つけます。ここに **[URL]** というフィールドがあるのがわかります。それを **Count** 関数のエンドポイントの正しい URL に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49910-177">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![TrackedObjectsBot プロジェクト AskingForCount ダイアログのトリガー エンドポイント構成](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="49910-179">最後に、**FindEntity** トリガーを探し、 *[HTTP 要求を送信します]* アクションを見つけて、 **[URL]** フィールドの URL を **Find** 関数のエンドポイントに変更します。</span><span class="sxs-lookup"><span data-stu-id="49910-179">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![TrackedObjectsBot プロジェクト FindEntity ダイアログのトリガー エンドポイント構成](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="49910-181">これですべてを設定したので、ボットをデプロイする準備ができました。</span><span class="sxs-lookup"><span data-stu-id="49910-181">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="49910-182">Bot Framework Composer をインストール済みであるため、そこから直接発行することができます。</span><span class="sxs-lookup"><span data-stu-id="49910-182">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="49910-183">[Bot Composer からのボットの発行](https://docs.microsoft.com/composer/how-to-publish-bot)に関する詳細情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49910-183">Learn more about [Publish a bot from Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="49910-184">トリガー フレーズ、新たな応答、会話の分岐を追加して、ボットを自由に試してみてください。</span><span class="sxs-lookup"><span data-stu-id="49910-184">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="49910-185">第 2 部 - すべてを Unity にまとめる</span><span class="sxs-lookup"><span data-stu-id="49910-185">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="49910-186">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="49910-186">Preparing the scene</span></span>

<span data-ttu-id="49910-187">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  > **MRTK.Tutorials.AzureCloudServices** >  **[Prefabs]\(プレハブ\)**  > **Manager** フォルダーの順に移動します。</span><span class="sxs-lookup"><span data-stu-id="49910-187">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![ChatBotManager プレハブが選択されている Unity プロジェクト ウィンドウ](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="49910-189">そこから、プレハブ **ChatBotManager** をシーン階層に移動します。</span><span class="sxs-lookup"><span data-stu-id="49910-189">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="49910-190">ChatBotManager をシーンに追加したら、**Chat Bot Manager** コンポーネントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="49910-190">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="49910-191">インスペクターには、入力する必要がある空の **[Direct Line Secret Key]\(ダイレクト ライン シークレット キー\)** フィールドがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="49910-191">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="49910-192">Azure portal から "*シークレット キー*" を取得できます。そのためには、このチュートリアルの最初の部分で作成した、種類が **[ボット チャンネル登録]** のリソースを検索します。</span><span class="sxs-lookup"><span data-stu-id="49910-192">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![新しく追加された ChatBotManager プレハブがまだ選択されている Unity](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="49910-194">次に、**ChatBotManager** オブジェクトを、**ChatBotPanel** オブジェクトにアタッチされた **ChatBotController** コンポーネントと接続します。</span><span class="sxs-lookup"><span data-stu-id="49910-194">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="49910-195">[Hierarchy]\(階層\) で **ChatBotPanel** を選択すると、空の **[Chat Bot Manager]** フィールドが表示されます。[Hierarchy]\(階層\) から **ChatBotManager** オブジェクトを空の **[Chat Bot Manager]** フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="49910-195">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![ChatBotPanel が構成された Unity](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="49910-197">次に、ユーザーが操作できるように **ChatBotPanel** を開く方法が必要です。</span><span class="sxs-lookup"><span data-stu-id="49910-197">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="49910-198">[Scene]\(シーン\) ウィンドウで、**MainMenu** オブジェクトに *[Chat Bot]\(チャット ボット\)* というサイド ボタンが表示されています。それを使用して、この問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="49910-198">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="49910-199">[Hierarchy]\(階層\) で **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** に移動し、インスペクターで *ButtonConfigHelper* スクリプトを見つけます。</span><span class="sxs-lookup"><span data-stu-id="49910-199">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="49910-200">そこには、**OnClick ()** イベント コールバックに空のスロットが表示されています。</span><span class="sxs-lookup"><span data-stu-id="49910-200">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="49910-201">**ChatBotPanel** をイベント スロットにドラッグ アンド ドロップします。ドロップダウン リストから *GameObject* に移動し、サブメニューで *SetActive (bool)* を選択して、チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="49910-201">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![ButtonChatBot が構成された Unity](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="49910-203">これで、メイン メニューからチャット ボットを開始できるようになり、それによって、シーンが使用できる状態になりました。</span><span class="sxs-lookup"><span data-stu-id="49910-203">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="49910-204">ボットをテストに配置する</span><span class="sxs-lookup"><span data-stu-id="49910-204">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="49910-205">追跡対象オブジェクトの数について質問する</span><span class="sxs-lookup"><span data-stu-id="49910-205">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="49910-206">まず、データベースに格納されている **追跡対象オブジェクト** の数をボットに質問するテストを行います。</span><span class="sxs-lookup"><span data-stu-id="49910-206">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="49910-207">今回は、アプリケーションを HoloLens 2 から実行する必要があります。お使いのシステムで "*音声合成*" などのサービスを使用できない場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="49910-207">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="49910-208">HoloLens 2 でアプリケーションを実行し、メイン メニューの横にある *[Chat Bot]\(チャット ボット\)* ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="49910-208">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="49910-209">ボットからあいさつがあったら、"**how many objects do we have?** " (オブジェクトは何個ありますか?) と質問します。</span><span class="sxs-lookup"><span data-stu-id="49910-209">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="49910-210">数量が通知され、会話が終了します。</span><span class="sxs-lookup"><span data-stu-id="49910-210">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="49910-211">追跡対象オブジェクトについて質問する</span><span class="sxs-lookup"><span data-stu-id="49910-211">Asking about a tracked object</span></span>

<span data-ttu-id="49910-212">ここで、アプリケーションをもう一度実行します。今度は、"**find me a tracked object**" (追跡対象オブジェクトを検索) と依頼します。ボットから名前をたずねられるので、"car" (車) と答えるか、データベース内に存在することがわかっている他の "*追跡対象オブジェクト*" の名前を答えます。</span><span class="sxs-lookup"><span data-stu-id="49910-212">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="49910-213">ボットから、説明などの詳細情報と、空間アンカーが割り当てられているかどうかが通知されます。</span><span class="sxs-lookup"><span data-stu-id="49910-213">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="49910-214">存在しない "**追跡対象オブジェクト**" について質問してみて、ボットがどのように応答するかを聞いてください。</span><span class="sxs-lookup"><span data-stu-id="49910-214">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="49910-215">結論</span><span class="sxs-lookup"><span data-stu-id="49910-215">Congratulations</span></span>

<span data-ttu-id="49910-216">このチュートリアルでは、Azure Bot Framework を使用して、自然言語での会話によってアプリケーションを操作する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="49910-216">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="49910-217">ご自身のボットを開発する方法と、それを実行するためのすべての可動要素について学習しました。</span><span class="sxs-lookup"><span data-stu-id="49910-217">You learned how to develop your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="49910-218">まとめ</span><span class="sxs-lookup"><span data-stu-id="49910-218">Conclusion</span></span>

<span data-ttu-id="49910-219">このチュートリアル シリーズを通して、**Azure Cloud Services** を使用してご自身のアプリケーションに新しい優れた機能を取り入れる方法を経験しました。</span><span class="sxs-lookup"><span data-stu-id="49910-219">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="49910-220">**Azure Storage** を使用してクラウドにデータと画像を格納すること、**Azure Custom Vision** を使用して画像を関連付け、モデルをトレーニングすること、**Azure Spatial Anchors** を使用してローカル コンテキストにオブジェクトを配置すること、**LUIS を搭載した Azure Bot Framework** を実装し、新しい自然な対話のパターンに対応した会話ボットを追加することができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="49910-220">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>
