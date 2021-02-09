---
title: インテントの設定と自然言語の理解
description: このコースを完了すると、Mixed Reality アプリケーションで意図と自然言語の理解を設定する方法がわかります。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー, 音声認識, Windows 10, LUIS, LUIS ポータル, 意図, エンティティ, 発話, 自然言語の理解
ms.localizationpriority: high
ms.openlocfilehash: 49e2b44000add22e924d9552f60b63ac1ac30288
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590364"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4.意図と自然言語の理解の設定

このチュートリアルでは、Azure 音声サービスの意図認識について説明します。 意図認識を使用すると、Microsoft のアプリケーションに AI 搭載の音声コマンドを実装でき、ユーザーは明確でない音声コマンドを発話しても、システムにその意図を理解させることができます。

## <a name="objectives"></a>目標

* LUIS ポータルで意図、エンティティ、および発話を設定する方法を理解する
* アプリケーションで意図と自然言語の理解を実装する方法を理解する

## <a name="preparing-the-scene"></a>シーンの準備

[Hierarchy]\(階層\) ウィンドウで、**Lunarcom** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、 **[コンポーネントの追加]** ボタンを使用して、**Lunarcom Intent Recognizer (Script)** コンポーネントを Lunarcom オブジェクトに追加します。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

[プロジェクト] ウィンドウで、 **[資産]**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)**  >  **[RocketLauncher]** フォルダーで、**RocketLauncher_Complete** プレハブを [Hierarchy]\(階層\) ウィンドウにドラッグし、カメラの前の適切な場所に配置します。次に例を示します。

* [変換] の **[位置]** X = 0、Y =-0.4、Z = 1
* [変換] の **[回転]** X = 0、Y = 90、Z = 0

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

[Hierarchy]\(階層\) ウィンドウで、**Lunarcom** オブジェクトをもう一度選択し、 **[RocketLauncher_Complete]**  >  **[Button]\(ボタン\)** オブジェクトを展開し、 **[Buttons]\(ボタン\)** オブジェクトの子オブジェクトをそれぞれ対応する **[Lunar Launcher Buttons]\(月着陸船ランチャー ボタン\)** フィールドに割り当てます。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a>Azure Language Understanding リソースの作成

このセクションでは、次のセクションで作成する Language Understanding Intelligent Service (LUIS) アプリ用の Azure 予測リソースを作成します。

<a href="https://portal.azure.com" target="_blank">Azure</a> にサインインし、 **[Create a resource]\(リソースの作成\)** をクリックします。 次に、 **[Language Understanding]** を検索して選択します。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

**[作成]** ボタンをクリックして、このサービスのインスタンスを作成します。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

[作成] ページで、 **[予測]** オプションをクリックし、次の値を入力します。

* **[サブスクリプション]** では、試用版のサブスクリプションをお持ちの場合は **[Free Trail]\(無料試用版\)** を選択します。それ以外の場合は、他のいずれかのサブスクリプションを選択します
* **[リソース グループ]** で **[新規作成]** リンクをクリックし、適切な名前 (*MRKT-Tutorials* など) を入力して、 **[OK]** をクリックします

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> このドキュメントの執筆時点では、次のセクションで Language Understanding Intelligent Service (LUIS) を作成すると、作成試用版キーが LUIS 内で自動的に生成されるため、作成リソースを作成する必要はありません。

> [!TIP]
> Azure アカウントに別の適切なリソース グループが既にある場合 ([Azure Spatial Anchors](mr-learning-asa-01.md) チュートリアルを完了している場合など)、新しいリソース グループを作成する代わりに、それを使用できます。

引き続き [作成] ページで、次の値を入力します。

* **[名前]** には、サービスの適切な名前 (*MRTK-Tutorials-AzureSpeechServices* など) を入力します
* **[Prediction location]\(予測の場所\)** では、アプリ ユーザーの物理的な場所に近い場所 ([ *(米国) 米国西部*] など) を選択します
* **[予測価格レベル]** では、このチュートリアルの場合は **[F0 (5 Calls per second, 10K Calls per month)]\(F0 (1 秒あたり 5 回の呼び出し、1 か月あたり 1 万回の呼び出し)\)** を選択します

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

次に、 **[確認および作成]** タブをクリックし、詳細を確認してから、ページの下部にある **[作成]** ボタンをクリックしてリソースを作成し、新しいリソース グループも (作成するように構成した場合は) 作成します。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> [作成] ボタンをクリックした後、サービスが作成されるまで待つ必要があります。これには数分かかる場合があります。

リソースの作成プロセスが完了すると、 **[デプロイが完了しました]** というメッセージが表示されます。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a>Language Understanding Intelligent Service (LUIS) の作成

このセクションでは、LUIS アプリを作成し、その予測モデルを構成してトレーニングし、前の手順で作成した Azure 予測リソースに接続します。

具体的には、ユーザーがアクションを実行する必要があると言った場合に、ユーザーが参照しているボタンに応じて、シーン内の 3 つの赤いボタンのいずれかの Interactable.OnClick() イベントがアプリでトリガーされるという意図を作成します。

たとえば、ユーザーが "**go ahead and launch the rocket**" (先へ進めて、ロケットを発射) と言った場合、アプリでは "**go ahead**" が何らかの **アクション** を実行する必要があることを意味することと、**ターゲット** に対するInteractable.OnClick() イベントがその **発射** ボタンにあることが予測されます。

これを実現するには、主に次の手順を実行します。

1. LUIS アプリの作成
2. 意図の作成
3. サンプル発話の作成
4. エンティティの作成
5. サンプル発話へのエンティティの割り当て
6. アプリのトレーニング、テスト、発行
7. アプリへの Azure 予測リソースの割り当て

### <a name="1-create-a-luis-app"></a>1.LUIS アプリの作成

前のセクションで Azure リソースを作成するときに使用したものと同じユーザー アカウントを使用して、<a href="https://www.luis.ai" target="_blank">LUIS</a> にサインインし、国を選択して、使用条件に同意します。 次の手順では、**Azure アカウントをリンクする** ように求められたら、代わりに Azure 作成リソースを使用するために、 **[Continue using your trial key]\(試用版キーを引き続き使用する\)** を選択します。

> [!NOTE]
> LUIS に既にサインアップしていて、作成試用版キーの有効期限が切れている場合は、ドキュメント「[Azure リソース作成キーに移行する](/azure/cognitive-services/luis/luis-migration-authoring)」を参照して、LUIS 作成リソースを Azure に切り替えることができます。

サインインしたら、 **[新しいアプリ]** をクリックし、 **[新しいアプリの作成]** ポップアップ ウィンドウに次の値を入力します。

* **[名前]** には、適切な名前 (*MRTK Tutorials - AzureSpeechServices* など) を入力します
* **[カルチャ]** では、 **[英語]** を選択します
* **[説明]** には、必要に応じて適切な説明を入力します
* **[予測リソース]** で、Azure portal で作成された予測リソースをドロップダウン リストで選択します。

次に、 **[完了]** ボタンをクリックして、新しいアプリを作成します。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

新しいアプリが作成されると、そのアプリの **[ダッシュボード]** ページが表示されます。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a>2.意図の作成

[ダッシュボード] ページで、[ビルド] > [App Assets]\(アプリ アセット\) > **[意図]** ページに移動し、 **[作成]** をクリックして、 **[Create new intent]\(新しい意図の作成\)** ポップアップ ウィンドウで次の値を入力します。

* **[Intent name]\(意図名\)** に「**PressButton**」と入力します

次に、 **[完了]** ボタンをクリックして、新しい意図を作成します。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> このチュートリアルでは、Unity プロジェクトでこの意図がその名前によって参照されます。つまり、'PressButton' です。 そのため、意図にまったく同じ名前を付けることが非常に重要です。

新しい意図が作成されると、その意図のページが表示されます。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a>3.サンプル発話の作成

**[PressButton]** 意図の **[Example utterance]\(サンプル発話\)** の一覧に、次のサンプル発話を追加します。

* activate launch sequence (発射手順を作動)
* show me a placement hint (配置のヒントを表示)
* initiate the launch sequence (発射手順を開始)
* press placement hints button (配置のヒント ボタンを押す)
* give me a hint (ヒントを表示)
* push the launch button (発射ボタンを押す)
* i need a hint (ヒントが必要)
* press the reset button (リセット ボタンを押す)
* time to reset the experience (エクスペリエンスをリセットする時間を計る)
* go ahead and launch the rocket (先へ進めて、ロケットを発射)

すべてのサンプル発話を追加すると、[PressButton] 意図ページは次のようになります。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> このチュートリアルでは、Unity プロジェクトで "hint"、"hints"、"reset"、および "launch" という単語が参照されます。 そのため、これらの単語をまったく同じようにつづることが非常に重要です。

### <a name="4-create-entities"></a>4.エンティティの作成

PressButton の意図ページから、[ビルド] > [App Assets]\(アプリ アセット\) > **[エンティティ]** ページに移動し、 **[作成]** をクリックして、 **[新しいエンティティの作成]** ポップアップ ウィンドウで次の値を入力します。

* **[エンティティ名]** には、「**Action**」と入力します
* **[エンティティ型]** で、 **[Machine learned]\(機械学習\)** を選択します

**[作成]** ボタンをクリックして、新しいエンティティを作成します。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

前の手順を **繰り返して**、**Target** という名前の別のエンティティを作成します。これで、Action と Target という名前の 2 つのエンティティが設定されます。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> このチュートリアルでは、Unity プロジェクトでこれらのエンティティがその名前によって参照されます。つまり、'Action' と 'Target' です。 そのため、エンティティにまったく同じ名前を付けることが非常に重要です。

### <a name="5-assign-entities-to-the-example-utterances"></a>5.サンプル発話へのエンティティの割り当て

[エンティティ] ページから **[PressButton]** 意図ページに戻ります。

[PressButton] 意図ページに戻ったら、単語 **go** をクリックしてから、単語 **ahead** をクリックします。次に、コンテキスト ポップアップ メニューから **[Action (Simple)]\(アクション (シンプル)\)** を選択して、**go ahead** に **Action** エンティティ値としてラベルを付けます。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

これで、**go ahead** という語句が **Action** エンティティ値として定義されました。 go ahead という語句の下にアクション エンティティの値が表示されます。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> 上の画像のラベルの下に表示される赤い線は、エンティティ値が予測されていないことを示しています。これは、次のセクションでモデルをトレーニングすると解決します。

次に、単語 **launch** をクリックし、コンテキスト ポップアップ メニューから **[Target (Simple)]\(ターゲット (シンプル)\)** を選択して、**launch** に **Target** エンティティ値としてラベルを付けます。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

**launch** という単語が **Target** エンティティの値として定義されるようになります。これで、単語 launch の下で Target エンティティの値がわかります。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

PressButton 意図のサンプル発話の "go ahead and launch the rocket" は、次のように予測されるように構成されました。

* 意図:PressButton
* Action エンティティ: go ahead
* Target エンティティ: launch

前の 2 段階のプロセスを **繰り返して**、Action および Target エンティティ ラベルを各サンプル発話に割り当てます。次の単語には **Target** エンティティというラベルを付ける必要があることに注意してください。

* **hint** (Unity プロジェクトの HintsButton をターゲットにします)
* **hints** (Unity プロジェクトの HintsButton をターゲットにします)
* **reset** (Unity プロジェクトの ResetButton をターゲットにします)
* **launch** (Unity プロジェクトの LaunchButton をターゲットにします)

すべてのサンプル発話にラベルを付けると、[PressButton] 意図ページは次のようになります。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

### <a name="6-train-test-and-publish-the-app"></a>6.アプリのトレーニング、テスト、発行

アプリをトレーニングするには、 **[トレーニング]** ボタンをクリックし、トレーニング プロセスが完了するまで待ちます。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> 上の画像に示されているように、すべてのラベルの下の赤い線が削除され、すべてのエンティティ値が予測されたことが示されています。 また、[トレーニング] ボタンの左側にある状態アイコンが赤から緑に変わっていることにも注目してください。

トレーニングの処理が完了したら、 **[テスト]** ボタンをクリックし、「**go ahead and launch the rocket**」と入力して、Enter キーを押します。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

テスト発話が処理されたら、 **[検査]** をクリックして、テスト結果を確認します。

* 意図:PressButton (98.5% の確実性)
* Action エンティティ: go ahead
* Target エンティティ: launch

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

アプリを発行するには、右上にある **[発行]** ボタンをクリックし、 **[Choose your publishing slot and settings]\(発行スロットと設定を選択する\)** ポップアップ ウィンドウで、 **[Production]\(運用\)** を選択して **[完了]** ボタンをクリックします。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

発行プロセスが完了するまで待ちます。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

[管理] > [アプリケーションの設定] > **[Azure リソース]** ページに移動すると、[Azure リソース] ページは次のようになります。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-6.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a>Unity プロジェクトを LUIS アプリに接続する

[管理] > [アプリケーションの設定] > **[Azure リソース]** ページで、**コピー** アイコンをクリックして、**サンプル クエリ** をコピーします。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

Unity プロジェクトに戻り、[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択し、次に [Inspector]\(インスペクター\) ウィンドウで **Lunarcom Intent Recognizer (Script)** コンポーネントを見つけ、次のように構成します。

* 前の手順でコピーした **サンプル クエリ** を **[LUIS Endpoint]\(LUIS エンドポイント\)** フィールドに貼り付けます。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a>意図認識のテストと改善

Unity エディターで意図認識を直接使用するには、開発用コンピューターでディクテーションを使用できるようにする必要があります。 この設定を確認するには、Windows の **[設定]** を開き、 **[プライバシー]**  >  **[音声認識]** を選択し **[オンライン音声認識]** がオンになっていることを確認します。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

これで、ゲーム モードに入ったら、まずロケット ボタンを押すと、意図認識をテストできます。 次に、お使いのコンピューターにマイクがあると仮定して、最初のサンプル発話の **go ahead and launch the rocket** を声に出すと、宇宙への LunarModule の発射が確認されます。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

**サンプル発話** をすべて試してから、**サンプル発話のバリエーション** をいくつかと、**ランダムな発話** をいくつか試してみてください。

次に、<a href="https://www.luis.ai" target="_blank">LUIS</a> に戻り、[ビルド] > [Improve app performance]\(アプリのパフォーマンスの向上\) > **[Review endpoint utterances]\(エンドポイントの発話の確認\)** ページに移動し、**トグル** ボタンを使用して既定のエンティティ ビューから **[Tokens View]\(トークン ビュー\)** に切り替え、発話を確認します。

* **[Utterance]\(発話\)** 列では、必要に応じて、意図に合うように割り当てられたラベルの変更や削除を行います
* **[Aligned intent]\(連携している意図\)** 列では、意図が正しいことを確認します
* **[Add/Delete]\(追加/削除\)** 列では、緑色のチェック マーク ボタンをクリックして発話を追加するか、赤い [x] ボタンをクリックして削除します

必要な数の発話を確認したら、 **[トレーニング]** ボタンをクリックしてモデルを再トレーニングし、 **[発行]** ボタンをクリックして更新されたアプリを再発行します。

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> エンドポイントの発話が PressButton 意図と連携していないが、その発話に意図がないことをモデルに認識させる必要がある場合は、[Aligned intent]\(連携している意図\) を [なし] に変更できます。

このプロセスを何度でも **繰り返して**、アプリ モデルを向上させます。

## <a name="congratulations"></a>結論

これで、プロジェクトに AI 搭載の音声コマンドが設定されました。これにより、正確なコマンドを口に出さなくても、アプリケーションでユーザーの意図を認識できます。 デバイスでアプリケーションを実行して、機能が適切に動作していることを確認してください。