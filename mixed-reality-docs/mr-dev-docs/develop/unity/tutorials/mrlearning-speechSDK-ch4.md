---
title: Azure 音声認識サービス チュートリアル - 4. 意図と自然言語の理解の設定
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure Speech SDK を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 8cebe1fb203aeed9a262a2e9f482993b4775e0a6
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91701306"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="47036-105">4.意図と自然言語の理解の設定</span><span class="sxs-lookup"><span data-stu-id="47036-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="47036-106">このチュートリアルでは、Azure 音声サービスの意図認識について説明します。</span><span class="sxs-lookup"><span data-stu-id="47036-106">In this tutorial, you will explore the Azure Speech Service's intent recognition.</span></span> <span data-ttu-id="47036-107">意図認識を使用すると、Microsoft のアプリケーションに AI 搭載の音声コマンドを実装でき、ユーザーは明確でない音声コマンドを発話しても、システムにその意図を理解させることができます。</span><span class="sxs-lookup"><span data-stu-id="47036-107">The intent recognition allows you to equip our application with AI-powered speech commands, where users can say non-specific speech commands and still have their intent understood by the system.</span></span>

## <a name="objectives"></a><span data-ttu-id="47036-108">目標</span><span class="sxs-lookup"><span data-stu-id="47036-108">Objectives</span></span>

* <span data-ttu-id="47036-109">LUIS ポータルで意図、エンティティ、および発話を設定する方法を理解する</span><span class="sxs-lookup"><span data-stu-id="47036-109">Learn how to set up intent, entities, and utterances in the LUIS portal</span></span>
* <span data-ttu-id="47036-110">アプリケーションで意図と自然言語の理解を実装する方法を理解する</span><span class="sxs-lookup"><span data-stu-id="47036-110">Learn how to implement intent and natural language understanding in our application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="47036-111">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="47036-111">Preparing the scene</span></span>

<span data-ttu-id="47036-112">[Hierarchy]\(階層\) ウィンドウで、 **Lunarcom** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、 **[コンポーネントの追加]** ボタンを使用して、 **Lunarcom Intent Recognizer (Script)** コンポーネントを Lunarcom オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="47036-112">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Intent Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

<span data-ttu-id="47036-114">[プロジェクト] ウィンドウで、 **[資産]**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)**  >  **[RocketLauncher]** フォルダーで、 **RocketLauncher_Complete** プレハブを [Hierarchy]\(階層\) ウィンドウにドラッグし、カメラの前の適切な場所に配置します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="47036-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher_Complete** prefab into your Hierarchy window, and place it at a suitable location in front of the camera, for example:</span></span>

* <span data-ttu-id="47036-115">[変換] の **[位置]** X = 0、Y =-0.4、Z = 1</span><span class="sxs-lookup"><span data-stu-id="47036-115">Transform **Position** X = 0, Y = -0.4, Z = 1</span></span>
* <span data-ttu-id="47036-116">[変換] の **[回転]** X = 0、Y = 90、Z = 0</span><span class="sxs-lookup"><span data-stu-id="47036-116">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

<span data-ttu-id="47036-118">[Hierarchy]\(階層\) ウィンドウで、 **Lunarcom** オブジェクトをもう一度選択し、 **[RocketLauncher_Complete]**  >  **[Button]\(ボタン\)** オブジェクトを展開し、 **[Buttons]\(ボタン\)** オブジェクトの子オブジェクトをそれぞれ対応する **[Lunar Launcher Buttons]\(月着陸船ランチャー ボタン\)** フィールドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="47036-118">In the Hierarchy window, select the **Lunarcom** object again, then expand the **RocketLauncher_Complete** > **Button** object and assign each of the **Buttons** object's child objects to the corresponding **Lunar Launcher Buttons** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a><span data-ttu-id="47036-120">Azure Language Understanding リソースの作成</span><span class="sxs-lookup"><span data-stu-id="47036-120">Creating the Azure Language Understanding resource</span></span>

<span data-ttu-id="47036-121">このセクションでは、次のセクションで作成する Language Understanding Intelligent Service (LUIS) アプリ用の Azure 予測リソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="47036-121">In this section, you will create an Azure prediction resource for the Language Understanding Intelligent Service (LUIS) app you will create in the next section.</span></span>

<span data-ttu-id="47036-122"><a href="https://portal.azure.com" target="_blank">Azure</a> にサインインし、 **[Create a resource]\(リソースの作成\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="47036-122">Sign in to <a href="https://portal.azure.com" target="_blank">Azure</a> and click **Create a resource** .</span></span> <span data-ttu-id="47036-123">次に、 **[Language Understanding]** を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="47036-123">Then search for and select **Language Understanding** :</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

<span data-ttu-id="47036-125">**[作成]** ボタンをクリックして、このサービスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="47036-125">Click the **Create** button to create an instance of this service:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

<span data-ttu-id="47036-127">[作成] ページで、 **[予測]** オプションをクリックし、次の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="47036-127">On the Create page, click the **Prediction** option and enter the following values:</span></span>

* <span data-ttu-id="47036-128">**[サブスクリプション]** では、試用版のサブスクリプションをお持ちの場合は **[Free Trail]\(無料試用版\)** を選択します。それ以外の場合は、他のいずれかのサブスクリプションを選択します</span><span class="sxs-lookup"><span data-stu-id="47036-128">For **Subscription** , select **Free Trail** if you have a trial subscription, otherwise, select one of your other subscriptions</span></span>
* <span data-ttu-id="47036-129">**[リソース グループ]** では、 **[新規作成]** リンクをクリックし、適切な名前 ( *MRKT-Tutorials* など) を入力して、 **[OK]** をクリックします</span><span class="sxs-lookup"><span data-stu-id="47036-129">For the **Resource group** , click the **Create new** link, enter a suitable name, for example, *MRKT-Tutorials* , and then click the **OK**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="47036-131">このドキュメントの執筆時点では、次のセクションで Language Understanding Intelligent Service (LUIS) を作成すると、作成試用版キーが LUIS 内で自動的に生成されるため、作成リソースを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="47036-131">As of the time of this writing, you do not need to create an authoring resource because an authoring trial key will automatically be generated within LUIS when you create the Language Understanding Intelligent Service (LUIS) in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="47036-132">Azure アカウントに別の適切なリソース グループが既にある場合 ([Azure Spatial Anchors](mr-learning-asa-01.md) チュートリアルを完了している場合など)、新しいリソース グループを作成する代わりに、それを使用できます。</span><span class="sxs-lookup"><span data-stu-id="47036-132">If you already have another suitable resource group in your Azure account, for example, if you completed the [Azure Spatial Anchors](mr-learning-asa-01.md) tutorial, you may use this resource group instead of creating a new one.</span></span>

<span data-ttu-id="47036-133">引き続き [作成] ページで、次の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="47036-133">While still on the Create page, enter the following values:</span></span>

* <span data-ttu-id="47036-134">**[名前]** には、サービスの適切な名前 ( *MRTK-Tutorials-AzureSpeechServices* など) を入力します</span><span class="sxs-lookup"><span data-stu-id="47036-134">For **Name** , enter a suitable name for the service, for example, *MRTK-Tutorials-AzureSpeechServices*</span></span>
* <span data-ttu-id="47036-135">**[Prediction location]\(予測の場所\)** では、アプリ ユーザーの物理的な場所に近い場所 ([ *(米国) 米国西部* ] など) を選択します</span><span class="sxs-lookup"><span data-stu-id="47036-135">For **Prediction location** , choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="47036-136">**[予測価格レベル]** では、このチュートリアルの場合は **[F0 (5 Calls per second, 10K Calls per month)]\(F0 (1 秒あたり 5 回の呼び出し、1 か月あたり 1 万回の呼び出し)\)** を選択します</span><span class="sxs-lookup"><span data-stu-id="47036-136">For **Prediction pricing tier** , for the purpose of this tutorial, select **F0 (5 Calls per second, 10K Calls per month)**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

<span data-ttu-id="47036-138">次に、 **[Review + create]\(確認および作成\)** タブに移動し、詳細を確認してから、ページの下部にある **[作成]** ボタンをクリックしてリソースを作成し、新しいリソース グループも (作成するように構成した場合は) 作成します。</span><span class="sxs-lookup"><span data-stu-id="47036-138">Next, go to the **Review + create** tab, review the details, and then click the **Create** button, located at the bottom of the page, to create the resource, as well as, the new resource group if you configured one to be created:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> <span data-ttu-id="47036-140">[作成] ボタンをクリックした後、サービスが作成されるまで待つ必要があります。これには数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="47036-140">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

<span data-ttu-id="47036-141">リソースの作成プロセスが完了すると、 **[デプロイが完了しました]** というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="47036-141">Once the resource creation process is completed, you will see the message **Your deployment is complete** :</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a><span data-ttu-id="47036-143">Language Understanding Intelligent Service (LUIS) の作成</span><span class="sxs-lookup"><span data-stu-id="47036-143">Creating the Language Understanding Intelligent Service (LUIS)</span></span>

<span data-ttu-id="47036-144">このセクションでは、LUIS アプリを作成し、その予測モデルを構成してトレーニングし、前の手順で作成した Azure 予測リソースに接続します。</span><span class="sxs-lookup"><span data-stu-id="47036-144">In this section, you will create a LUIS app, configure and train its prediction model, and connect it to the Azure prediction resource you created in the previous step.</span></span>

<span data-ttu-id="47036-145">具体的には、ユーザーがアクションを実行する必要があると言った場合に、ユーザーが参照しているボタンに応じて、シーン内の 3 つの赤いボタンのいずれかの Interactable.OnClick() イベントがアプリでトリガーされるという意図を作成します。</span><span class="sxs-lookup"><span data-stu-id="47036-145">Specifically, you will create an intent that if the user says an action should be taken, the app will trigger the Interactable.OnClick() event on one of the three red buttons in the scene, depending on which button the user references.</span></span>

<span data-ttu-id="47036-146">たとえば、ユーザーが " **go ahead and launch the rocket** " (先へ進めて、ロケットを発射) と言った場合、アプリでは " **go ahead** " が何らかの **アクション** を実行する必要があることを意味することと、 **ターゲット** に対するInteractable.OnClick() イベントがその **発射** ボタンにあることが予測されます。</span><span class="sxs-lookup"><span data-stu-id="47036-146">For example, if the user says **go ahead and launch the rocket** , the app will predict that **go ahead** means some **action** should be taken, and that the Interactable.OnClick() event to **target** is on the **launch** button.</span></span>

<span data-ttu-id="47036-147">これを実現するには、主に次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="47036-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="47036-148">LUIS アプリの作成</span><span class="sxs-lookup"><span data-stu-id="47036-148">Create a LUIS app</span></span>
2. <span data-ttu-id="47036-149">意図の作成</span><span class="sxs-lookup"><span data-stu-id="47036-149">Create intents</span></span>
3. <span data-ttu-id="47036-150">サンプル発話の作成</span><span class="sxs-lookup"><span data-stu-id="47036-150">Create example utterances</span></span>
4. <span data-ttu-id="47036-151">エンティティの作成</span><span class="sxs-lookup"><span data-stu-id="47036-151">Create entities</span></span>
5. <span data-ttu-id="47036-152">サンプル発話へのエンティティの割り当て</span><span class="sxs-lookup"><span data-stu-id="47036-152">Assign entities to the example utterances</span></span>
6. <span data-ttu-id="47036-153">アプリのトレーニング、テスト、発行</span><span class="sxs-lookup"><span data-stu-id="47036-153">Train, test, and publish the app</span></span>
7. <span data-ttu-id="47036-154">アプリへの Azure 予測リソースの割り当て</span><span class="sxs-lookup"><span data-stu-id="47036-154">Assign an Azure prediction resource to the app</span></span>

### <a name="1-create-a-luis-app"></a><span data-ttu-id="47036-155">1.LUIS アプリの作成</span><span class="sxs-lookup"><span data-stu-id="47036-155">1. Create a LUIS app</span></span>

<span data-ttu-id="47036-156">前のセクションで Azure リソースを作成するときに使用したものと同じユーザー アカウントを使用して、<a href="https://www.luis.ai" target="_blank">LUIS</a> にサインインし、国を選択して、使用条件に同意します。</span><span class="sxs-lookup"><span data-stu-id="47036-156">Using the same user account you used when creating the Azure resource in the previous section, sign in to <a href="https://www.luis.ai" target="_blank">LUIS</a>, select your country, and agree to the terms of use.</span></span> <span data-ttu-id="47036-157">次の手順では、 **Azure アカウントをリンクする** ように求められたら、代わりに Azure 作成リソースを使用するために、 **[Continue using your trial key]\(試用版キーを引き続き使用する\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="47036-157">In the next step, when asked to **Link your Azure account** , choose **Continue using your trial key** , to use an Azure authoring resource instead.</span></span>

> [!NOTE]
> <span data-ttu-id="47036-158">LUIS に既にサインアップしていて、作成試用版キーの有効期限が切れている場合は、ドキュメント「[Azure リソース作成キーに移行する](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring)」を参照して、LUIS 作成リソースを Azure に切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="47036-158">If you have already signed up for LUIS and your authoring trial key has expired, you can refer to the [Migrate to an Azure resource authoring key](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) documentation to switch your LUIS authoring resource to Azure.</span></span>

<span data-ttu-id="47036-159">サインインしたら、 **[マイ アプリ]** ページに移動し、 **[新しいアプリの作成]** をクリックして、 **[新しいアプリの作成]** ポップアップ ウィンドウに次の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="47036-159">Once signed in, navigate to the **My apps** page, then click **Create new app** and enter the following values in the **Create new app** popup window:</span></span>

* <span data-ttu-id="47036-160">**[名前]** には、適切な名前 ( *MRTK Tutorials - AzureSpeechServices* など) を入力します</span><span class="sxs-lookup"><span data-stu-id="47036-160">For **Name** , enter a suitable name, for example, *MRTK Tutorials - AzureSpeechServices*</span></span>
* <span data-ttu-id="47036-161">**[カルチャ]** では、 **[英語]** を選択します</span><span class="sxs-lookup"><span data-stu-id="47036-161">For **Culture** , select **English**</span></span>
* <span data-ttu-id="47036-162">**[説明]** には、必要に応じて適切な説明を入力します</span><span class="sxs-lookup"><span data-stu-id="47036-162">For **Description** , optionally enter a suitable description</span></span>

<span data-ttu-id="47036-163">次に、 **[完了]** ボタンをクリックして、新しいアプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="47036-163">Then click the **Done** button to create the new app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

<span data-ttu-id="47036-165">新しいアプリが作成されると、そのアプリの **[ダッシュボード]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="47036-165">When the new app has been created, you will be taken to that app's **Dashboard** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a><span data-ttu-id="47036-167">2.意図の作成</span><span class="sxs-lookup"><span data-stu-id="47036-167">2. Create intents</span></span>

<span data-ttu-id="47036-168">[ダッシュボード] ページで、[ビルド] > [App Assets]\(アプリ資産\) > **[意図]** ページに移動し、 **[Create new intent]\(新しい意図の作成\)** をクリックして、 **[Create new intent]\(新しい意図の作成\)** ポップアップ ウィンドウに次の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="47036-168">From the Dashboard page, navigate to the Build > App Assets > **Intents** page, then click **Create new intent** and enter the following value in the **Create new intent** popup window:</span></span>

* <span data-ttu-id="47036-169">**[Intent name]\(意図名\)** に「 **PressButton** 」と入力します</span><span class="sxs-lookup"><span data-stu-id="47036-169">For **Intent name** , enter **PressButton**</span></span>

<span data-ttu-id="47036-170">次に、 **[完了]** ボタンをクリックして、新しい意図を作成します。</span><span class="sxs-lookup"><span data-stu-id="47036-170">Then click the **Done** button to create the new intent:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> <span data-ttu-id="47036-172">このチュートリアルでは、Unity プロジェクトでこの意図がその名前によって参照されます。つまり、'PressButton' です。</span><span class="sxs-lookup"><span data-stu-id="47036-172">For the purpose of this tutorial, your Unity project will reference this intent by its name, i.e. 'PressButton'.</span></span> <span data-ttu-id="47036-173">そのため、意図にまったく同じ名前を付けることが非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="47036-173">Consequently, it is extremely important that you name your intent exactly the same.</span></span>

<span data-ttu-id="47036-174">新しい意図が作成されると、その意図のページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="47036-174">When the new intent has been created, you will be taken to that intent's page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a><span data-ttu-id="47036-176">3.サンプル発話の作成</span><span class="sxs-lookup"><span data-stu-id="47036-176">3. Create example utterances</span></span>

<span data-ttu-id="47036-177">**[PressButton]** 意図の **[Example utterance]\(サンプル発話\)** の一覧に、次のサンプル発話を追加します。</span><span class="sxs-lookup"><span data-stu-id="47036-177">To the **PressButton** intent's **Example utterance** list, add the following example utterances:</span></span>

* <span data-ttu-id="47036-178">activate launch sequence (発射手順を作動)</span><span class="sxs-lookup"><span data-stu-id="47036-178">activate launch sequence</span></span>
* <span data-ttu-id="47036-179">show me a placement hint (配置のヒントを表示)</span><span class="sxs-lookup"><span data-stu-id="47036-179">show me a placement hint</span></span>
* <span data-ttu-id="47036-180">initiate the launch sequence (発射手順を開始)</span><span class="sxs-lookup"><span data-stu-id="47036-180">initiate the launch sequence</span></span>
* <span data-ttu-id="47036-181">press placement hints button (配置のヒント ボタンを押す)</span><span class="sxs-lookup"><span data-stu-id="47036-181">press placement hints button</span></span>
* <span data-ttu-id="47036-182">give me a hint (ヒントを表示)</span><span class="sxs-lookup"><span data-stu-id="47036-182">give me a hint</span></span>
* <span data-ttu-id="47036-183">push the launch button (発射ボタンを押す)</span><span class="sxs-lookup"><span data-stu-id="47036-183">push the launch button</span></span>
* <span data-ttu-id="47036-184">i need a hint (ヒントが必要)</span><span class="sxs-lookup"><span data-stu-id="47036-184">i need a hint</span></span>
* <span data-ttu-id="47036-185">press the reset button (リセット ボタンを押す)</span><span class="sxs-lookup"><span data-stu-id="47036-185">press the reset button</span></span>
* <span data-ttu-id="47036-186">time to reset the experience (エクスペリエンスをリセットする時間を計る)</span><span class="sxs-lookup"><span data-stu-id="47036-186">time to reset the experience</span></span>
* <span data-ttu-id="47036-187">go ahead and launch the rocket (先へ進めて、ロケットを発射)</span><span class="sxs-lookup"><span data-stu-id="47036-187">go ahead and launch the rocket</span></span>

<span data-ttu-id="47036-188">すべてのサンプル発話を追加すると、[PressButton] 意図ページは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="47036-188">When all the example utterances have been added, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> <span data-ttu-id="47036-190">このチュートリアルでは、Unity プロジェクトで "hint"、"hints"、"reset"、および "launch" という単語が参照されます。</span><span class="sxs-lookup"><span data-stu-id="47036-190">For the purpose of this tutorial, your Unity project will reference the words 'hint', 'hints', 'reset', and 'launch'.</span></span> <span data-ttu-id="47036-191">そのため、これらの単語をまったく同じようにつづることが非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="47036-191">Consequently, it is extremely important that you spell these words in the exact same way.</span></span>

### <a name="4-create-entities"></a><span data-ttu-id="47036-192">4.エンティティの作成</span><span class="sxs-lookup"><span data-stu-id="47036-192">4. Create entities</span></span>

<span data-ttu-id="47036-193">[PressButton] 意図ページで、[ビルド] > [App Assets]\(アプリ資産\) > **[エンティティ]** ページに移動し、 **[新しいエンティティを作成する]** をクリックして、 **[新しいエンティティを作成する]** ポップアップ ウィンドウに次の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="47036-193">From the PressButton intent page, navigate to the Build > App Assets > **Entities** page, then click **Create new entity** and enter the following values in the **Create new entity** popup window:</span></span>

* <span data-ttu-id="47036-194">**[エンティティ名]** には、「 **Action** 」と入力します</span><span class="sxs-lookup"><span data-stu-id="47036-194">For **Entity name** , enter **Action**</span></span>
* <span data-ttu-id="47036-195">**[エンティティ型]** では、 **[シンプル]** を選択します</span><span class="sxs-lookup"><span data-stu-id="47036-195">For **Entity type** , select **Simple**</span></span>

<span data-ttu-id="47036-196">次に、 **[完了]** ボタンをクリックして、新しいエンティティを作成します。</span><span class="sxs-lookup"><span data-stu-id="47036-196">Then click the **Done** button to create the new entity:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

<span data-ttu-id="47036-198">前の手順を **繰り返して** 、 **Target** という名前の別のエンティティを作成します。これで、Action と Target という名前の 2 つのエンティティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="47036-198">**Repeat** the previous step to create another entity named **Target** , so you have two entities named Action and Target:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> <span data-ttu-id="47036-200">このチュートリアルでは、Unity プロジェクトでこれらのエンティティがその名前によって参照されます。つまり、'Action' と 'Target' です。</span><span class="sxs-lookup"><span data-stu-id="47036-200">For the purpose of this tutorial, your Unity project will reference these entities by their names, i.e. 'Action' and 'Target'.</span></span> <span data-ttu-id="47036-201">そのため、エンティティにまったく同じ名前を付けることが非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="47036-201">Consequently, it is extremely important that you name your entities exactly the same.</span></span>

### <a name="5-assign-entities-to-the-example-utterances"></a><span data-ttu-id="47036-202">5.サンプル発話へのエンティティの割り当て</span><span class="sxs-lookup"><span data-stu-id="47036-202">5. Assign entities to the example utterances</span></span>

<span data-ttu-id="47036-203">[エンティティ] ページから **[PressButton]** 意図ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="47036-203">From the Entities page, navigate back to the **PressButton** intent page.</span></span>

<span data-ttu-id="47036-204">[PressButton] 意図ページに戻ったら、単語 **go** をクリックしてから、単語 **ahead** をクリックします。次に、コンテキスト ポップアップ メニューから **[Action (Simple)]\(アクション (シンプル)\)** を選択して、 **go ahead** に **Action** エンティティ値としてラベルを付けます。</span><span class="sxs-lookup"><span data-stu-id="47036-204">Once back on the the PressButton intent page, click on the word **go** and then on the word **ahead** , and then select **Action (Simple)** from the contextual popup menu to label **go ahead** as an **Action** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

<span data-ttu-id="47036-206">これで、 **go ahead** という語句が **Action** エンティティ値として定義されました。</span><span class="sxs-lookup"><span data-stu-id="47036-206">The **go ahead** phrase is now defined as an **Action** entity value.</span></span> <span data-ttu-id="47036-207">Action エンティティ名の上にマウス カーソルを置くと、関連付けられている Action エンティティ値を表示できます。</span><span class="sxs-lookup"><span data-stu-id="47036-207">If you hover your mouse cursor above the Action entity name, you can see the associated Action entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> <span data-ttu-id="47036-209">上の画像のラベルの下に表示される赤い線は、エンティティ値が予測されていないことを示しています。これは、次のセクションでモデルをトレーニングすると解決します。</span><span class="sxs-lookup"><span data-stu-id="47036-209">The red line you see under the label in the image above indicates that the entity value has not been predicted, this will be resolved when you train the model in the next section.</span></span>

<span data-ttu-id="47036-210">次に、単語 **launch** をクリックし、コンテキスト ポップアップ メニューから **[Target (Simple)]\(ターゲット (シンプル)\)** を選択して、 **launch** に **Target** エンティティ値としてラベルを付けます。</span><span class="sxs-lookup"><span data-stu-id="47036-210">Next, click on the word **launch** , and then select **Target (Simple)** from the contextual popup menu to label **launch** as a **Target** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

<span data-ttu-id="47036-212">これで、 **launch** という単語が **Target** エンティティ値として定義されました。</span><span class="sxs-lookup"><span data-stu-id="47036-212">The **launch** word is now defined as a **Target** entity value.</span></span> <span data-ttu-id="47036-213">Target エンティティ名の上にマウス カーソルを置くと、関連付けられている Target エンティティ値を表示できます。</span><span class="sxs-lookup"><span data-stu-id="47036-213">If you hover your mouse cursor above the Target entity name, you can see the associated Target entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

<span data-ttu-id="47036-215">PressButton 意図のサンプル発話の "go ahead and launch the rocket" は、次のように予測されるように構成されました。</span><span class="sxs-lookup"><span data-stu-id="47036-215">The PressButton intent example utterance 'go ahead and launch the rocket' is now configured to be predicted as follows:</span></span>

* <span data-ttu-id="47036-216">意図:PressButton</span><span class="sxs-lookup"><span data-stu-id="47036-216">Intent: PressButton</span></span>
* <span data-ttu-id="47036-217">Action エンティティ: go ahead</span><span class="sxs-lookup"><span data-stu-id="47036-217">Action entity: go ahead</span></span>
* <span data-ttu-id="47036-218">Target エンティティ: launch</span><span class="sxs-lookup"><span data-stu-id="47036-218">Target entity: launch</span></span>

<span data-ttu-id="47036-219">前の 2 段階のプロセスを **繰り返して** 、Action および Target エンティティ ラベルを各サンプル発話に割り当てます。次の単語には **Target** エンティティというラベルを付ける必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="47036-219">**Repeat** the previous two-step process to assign an Action and a Target entity label to each of the example utterances, keeping in mind that the following words should be labeled as **Target** entities:</span></span>

* <span data-ttu-id="47036-220">**hint** (Unity プロジェクトの HintsButton をターゲットにします)</span><span class="sxs-lookup"><span data-stu-id="47036-220">**hint** (targets the HintsButton in the Unity project)</span></span>
* <span data-ttu-id="47036-221">**hints** (Unity プロジェクトの HintsButton をターゲットにします)</span><span class="sxs-lookup"><span data-stu-id="47036-221">**hints** (targets HintsButton in the Unity project)</span></span>
* <span data-ttu-id="47036-222">**reset** (Unity プロジェクトの ResetButton をターゲットにします)</span><span class="sxs-lookup"><span data-stu-id="47036-222">**reset** (targets the ResetButton in the Unity project)</span></span>
* <span data-ttu-id="47036-223">**launch** (Unity プロジェクトの LaunchButton をターゲットにします)</span><span class="sxs-lookup"><span data-stu-id="47036-223">**launch** (targets the LaunchButton in the Unity project)</span></span>

<span data-ttu-id="47036-224">すべてのサンプル発話にラベルを付けると、[PressButton] 意図ページは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="47036-224">When all the example utterances have been labeled, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

<span data-ttu-id="47036-226">適切なエンティティが割り当てられていることを再確認する別の方法として、 **[View options]\(表示オプション\)** メニューをクリックして、ビューを **[Show entity values]\(エンティティ値の表示\)** に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="47036-226">For an alternative way to double-check that you have assigned the correct entities, click the **View options** menu and switch the view to **Show entity values** :</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

<span data-ttu-id="47036-228">エンティティ値を表示するように設定したビューでは、ラベル付けされた単語や語句の上にマウス カーソルを置くと、割り当てられているエンティティ名をすぐに確認できます。</span><span class="sxs-lookup"><span data-stu-id="47036-228">Now, with the view set to show entity values, you can hover the mouse courser over the labeled words and phrases to quickly verify the assigned entity name:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a><span data-ttu-id="47036-230">6.アプリのトレーニング、テスト、発行</span><span class="sxs-lookup"><span data-stu-id="47036-230">6. Train, test, and publish the app</span></span>

<span data-ttu-id="47036-231">アプリをトレーニングするには、 **[トレーニング]** ボタンをクリックし、トレーニング プロセスが完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="47036-231">To train the app, click the **Train** button and wait for the training process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> <span data-ttu-id="47036-233">上の画像に示されているように、すべてのラベルの下の赤い線が削除され、すべてのエンティティ値が予測されたことが示されています。</span><span class="sxs-lookup"><span data-stu-id="47036-233">As you can see in the image above, the red lines under all the labels have been removed, indicating that all the entity values have been predicted.</span></span> <span data-ttu-id="47036-234">また、[トレーニング] ボタンの左側にある状態アイコンが赤から緑に変わっていることにも注目してください。</span><span class="sxs-lookup"><span data-stu-id="47036-234">Also notice that the status icon to the left of the Train button has changed color from red to green.</span></span>

<span data-ttu-id="47036-235">トレーニングの処理が完了したら、 **[テスト]** ボタンをクリックし、「 **go ahead and launch the rocket** 」と入力して、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="47036-235">When the training is finished processing, click the **Test** button, then type in **go ahead and launch the rocket** and press the Enter key:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

<span data-ttu-id="47036-237">テスト発話が処理されたら、 **[検査]** をクリックして、テスト結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="47036-237">When the test utterance has been processed, click **Inspect** to see the test result:</span></span>

* <span data-ttu-id="47036-238">意図:PressButton (98.5% の確実性)</span><span class="sxs-lookup"><span data-stu-id="47036-238">Intent: PressButton (with a 98.5% certainty)</span></span>
* <span data-ttu-id="47036-239">Action エンティティ: go ahead</span><span class="sxs-lookup"><span data-stu-id="47036-239">Action entity: go ahead</span></span>
* <span data-ttu-id="47036-240">Target エンティティ: launch</span><span class="sxs-lookup"><span data-stu-id="47036-240">Target entity: launch</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

<span data-ttu-id="47036-242">アプリを発行するには、右上にある **[発行]** ボタンをクリックし、 **[Choose your publishing slot and settings]\(発行スロットと設定の選択\)** ポップアップ ウィンドウで、 **[Production]\(実稼働\)** を選択し、 **[発行]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="47036-242">To publish the app, click the **Publish** button in the top right, then in the **Choose your publishing slot and settings** popup window, select **Production** and click the **Publish** button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

<span data-ttu-id="47036-244">発行プロセスが完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="47036-244">Wait for the publishing process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a><span data-ttu-id="47036-246">7.アプリへの Azure 予測リソースの割り当て</span><span class="sxs-lookup"><span data-stu-id="47036-246">7. Assign an Azure prediction resource to the app</span></span>

<span data-ttu-id="47036-247">[管理] > [アプリケーションの設定] > **[Azure リソース]** ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="47036-247">Navigate to the Manage > Application Settings > **Azure Resources** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

<span data-ttu-id="47036-249">[Azure リソース] ページで、 **[Add prediction resource]\(予測リソースの追加\)** ボタンをクリックし、 **[Assign a resource to your app]\(リソースをアプリに割り当てる\)** ポップアップ ウィンドウで次の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="47036-249">On the Azure Resources page, click the **Add prediction resource** button and select the following values in the **Assign a resource to your app** popup window:</span></span>

* <span data-ttu-id="47036-250">**[テナント名]** では、テナント名を選択します</span><span class="sxs-lookup"><span data-stu-id="47036-250">For **Tenant name** , select your tenant name</span></span>
* <span data-ttu-id="47036-251">**[サブスクリプション名]** では、以前、 [Azure Language Understanding リソースの作成](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)時に使用したものと同じサブスクリプションを選択します</span><span class="sxs-lookup"><span data-stu-id="47036-251">For **Subscription Name** , select the same subscription you used earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>
* <span data-ttu-id="47036-252">**[LUIS resource name]\(LUIS リソース名\)** では、以前、 [Azure Language Understanding リソースの作成](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)時に作成した予測リソースを選択します</span><span class="sxs-lookup"><span data-stu-id="47036-252">For **LUIS resource name** , select the prediction resource you created earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>

<span data-ttu-id="47036-253">次に、 **[リソースの割り当て]** ボタンをクリックして、アプリに Azure 予測リソースを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="47036-253">Then click the **Assign resource** button to assign the Azure prediction resource to your app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

<span data-ttu-id="47036-255">リソースが割り当てられると、[Azure リソース] ページは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="47036-255">When the resource has been assigned, your Azure Resources page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a><span data-ttu-id="47036-257">Unity プロジェクトを LUIS アプリに接続する</span><span class="sxs-lookup"><span data-stu-id="47036-257">Connecting the Unity project to the LUIS app</span></span>

<span data-ttu-id="47036-258">[管理] > [アプリケーションの設定] > **[Azure リソース]** ページで、 **コピー** アイコンをクリックして、 **サンプル クエリ** をコピーします。</span><span class="sxs-lookup"><span data-stu-id="47036-258">On the Manage > Application Settings > **Azure Resources** page, click the **copy** icon to copy the **Example Query** :</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

<span data-ttu-id="47036-260">Unity プロジェクトに戻り、[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択し、次に [Inspector]\(インスペクター\) ウィンドウで **Lunarcom Intent Recognizer (Script)** コンポーネントを見つけ、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="47036-260">Back in your Unity project, in the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Intent Recognizer (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="47036-261">前の手順でコピーした **サンプル クエリ** を **[LUIS Endpoint]\(LUIS エンドポイント\)** フィールドに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="47036-261">In the **LUIS Endpoint** field, past the **Example Query** you copied in the previous step:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a><span data-ttu-id="47036-263">意図認識のテストと改善</span><span class="sxs-lookup"><span data-stu-id="47036-263">Testing and improving the intent recognition</span></span>

<span data-ttu-id="47036-264">Unity エディターで意図認識を直接使用するには、開発用コンピューターでディクテーションを使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="47036-264">To use intent recognition directly in the Unity editor, you must allow your development computer to use dictation.</span></span> <span data-ttu-id="47036-265">この設定を確認するには、Windows の **[設定]** を開き、 **[プライバシー]**  >  **[音声認識]** を選択し **[オンライン音声認識]** がオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="47036-265">To verify this setting, open Windows **Settings** then choose **Privacy** > **Speech** and ensure **Online speech recognition** is turned on:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

<span data-ttu-id="47036-267">これで、ゲーム モードに入ったら、まずロケット ボタンを押すと、意図認識をテストできます。</span><span class="sxs-lookup"><span data-stu-id="47036-267">If you now enter Game mode, you can test the intent recognition by first pressing the rocket button.</span></span> <span data-ttu-id="47036-268">次に、お使いのコンピューターにマイクがあると仮定して、最初のサンプル発話の **go ahead and launch the rocket** を声に出すと、宇宙への LunarModule の発射が確認されます。</span><span class="sxs-lookup"><span data-stu-id="47036-268">Then, assuming your computer has a microphone, when you say the first example utterance, **go ahead and launch the rocket** , you will see the LunarModule launch into space:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

<span data-ttu-id="47036-270">**サンプル発話** をすべて試してから、 **サンプル発話のバリエーション** をいくつかと、 **ランダムな発話** をいくつか試してみてください。</span><span class="sxs-lookup"><span data-stu-id="47036-270">Try all the **example utterances** , then some **variation of the example utterances** , as well as, a few **random utterances** .</span></span>

<span data-ttu-id="47036-271">次に、 <a href="https://www.luis.ai" target="_blank">LUIS</a> に戻り、[ビルド] > [Improve app performance]\(アプリのパフォーマンスの向上\) > **[Review endpoint utterances]\(エンドポイントの発話の確認\)** ページに移動し、 **トグル** ボタンを使用して既定のエンティティ ビューから **[Tokens View]\(トークン ビュー\)** に切り替え、発話を確認します。</span><span class="sxs-lookup"><span data-stu-id="47036-271">Next, return to <a href="https://www.luis.ai" target="_blank">LUIS</a> and navigate to Build > Improve app performance > **Review endpoint utterances** page, use the **toggle** button to switch from the default Entities View to **Tokens View** , and then review the utterances:</span></span>

* <span data-ttu-id="47036-272">**[Utterance]\(発話\)** 列では、必要に応じて、意図に合うように割り当てられたラベルの変更や削除を行います</span><span class="sxs-lookup"><span data-stu-id="47036-272">In the **Utterance** column, change and remove the assigned labels as needed so they align with your intent</span></span>
* <span data-ttu-id="47036-273">**[Aligned intent]\(連携している意図\)** 列では、意図が正しいことを確認します</span><span class="sxs-lookup"><span data-stu-id="47036-273">In the **Aligned intent** column, verify that the intent is correct</span></span>
* <span data-ttu-id="47036-274">**[Add/Delete]\(追加/削除\)** 列では、緑色のチェック マーク ボタンをクリックして発話を追加するか、赤い [x] ボタンをクリックして削除します</span><span class="sxs-lookup"><span data-stu-id="47036-274">In the **Add/Delete** column, click the green check mark button to add the utterance or the red x button to delete it</span></span>

<span data-ttu-id="47036-275">必要な数の発話を確認したら、 **[トレーニング]** ボタンをクリックしてモデルを再トレーニングし、 **[発行]** ボタンをクリックして更新されたアプリを再発行します。</span><span class="sxs-lookup"><span data-stu-id="47036-275">When you have reviewed as many utterances as you like, click the **Train** button to retrain the model, then the **Publish** button to republish the updated app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> <span data-ttu-id="47036-277">エンドポイントの発話が PressButton 意図と連携していないが、その発話に意図がないことをモデルに認識させる必要がある場合は、[Aligned intent]\(連携している意図\) を [なし] に変更できます。</span><span class="sxs-lookup"><span data-stu-id="47036-277">If an endpoint utterance does not align with the PressButton intent, but you would like your model to know that the utterance has no intent, you can change the Aligned intent to None.</span></span>

<span data-ttu-id="47036-278">このプロセスを何度でも **繰り返して** 、アプリ モデルを向上させます。</span><span class="sxs-lookup"><span data-stu-id="47036-278">**Repeat** this process as many times as you like to improve your app model.</span></span>

## <a name="congratulations"></a><span data-ttu-id="47036-279">結論</span><span class="sxs-lookup"><span data-stu-id="47036-279">Congratulations</span></span>

<span data-ttu-id="47036-280">これで、プロジェクトに AI 搭載の音声コマンドが設定されました。これにより、正確なコマンドを口に出さなくても、アプリケーションでユーザーの意図を認識できます。</span><span class="sxs-lookup"><span data-stu-id="47036-280">Your project now have AI-powered speech commands, allowing your application to recognize the users' intent even if they do not utter precise commands.</span></span> <span data-ttu-id="47036-281">デバイスでアプリケーションを実行して、機能が適切に動作していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="47036-281">Run the application on your device to ensure the feature is working properly.</span></span>
