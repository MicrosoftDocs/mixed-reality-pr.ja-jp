---
title: Unreal での音声入力
description: HoloLens 2 デバイス向けの Unreal mixed reality アプリで音声入力、音声マッピング、および認識を設定して使用する方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、Unreal、Unreal Engine 4、UE4、HoloLens 2、音声、音声入力、音声認識、mixed reality、開発、機能、ドキュメント、ガイド、ホログラム、ゲーム開発、mixed reality ヘッドセット、windows mixed Reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: c7ac523258dc44aa261470aea8cdf21f32c915b2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010072"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="b756a-104">Unreal での音声入力</span><span class="sxs-lookup"><span data-stu-id="b756a-104">Voice Input in Unreal</span></span>

<span data-ttu-id="b756a-105">Unreal の音声入力を使用すると、ハンドジェスチャを使用しなくても、または HoloLens 2 のみがサポートされるようになります。</span><span class="sxs-lookup"><span data-stu-id="b756a-105">Voice input in Unreal allows you to interact with a hologram without having to use hand gestures and is only supported HoloLens 2.</span></span> <span data-ttu-id="b756a-106">HoloLens 2 での音声入力は、他のすべてのユニバーサル Windows アプリで音声をサポートするのと同じエンジンによって機能しますが、より限定的なエンジンを使用して音声入力を処理します。</span><span class="sxs-lookup"><span data-stu-id="b756a-106">Voice input on HoloLens 2 is powered by the same engine that supports speech in all other Universal Windows Apps, but Unreal uses a more limited engine to process voice input.</span></span> <span data-ttu-id="b756a-107">これにより、次のセクションで説明するように、Unreal の音声入力機能が定義済みの音声マッピングに限定されます。</span><span class="sxs-lookup"><span data-stu-id="b756a-107">This limits voice input features in Unreal to predefined speech mappings, which are covered in the following sections.</span></span> 

## <a name="enabling-speech-recognition"></a><span data-ttu-id="b756a-108">音声認識を有効にする</span><span class="sxs-lookup"><span data-stu-id="b756a-108">Enabling Speech Recognition</span></span>

<span data-ttu-id="b756a-109">HoloLens で音声認識を有効にするには:</span><span class="sxs-lookup"><span data-stu-id="b756a-109">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="b756a-110">[プロジェクトの設定] を選択して **> プラットフォーム > HoloLens > 機能** を選択し、 **マイク** を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b756a-110">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="b756a-111">[設定] で音声認識を有効にし、[**プライバシー] > [>** ] を選択します。 </span><span class="sxs-lookup"><span data-stu-id="b756a-111">Enabled speech recognition in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="b756a-112">音声認識は常に、 **設定** アプリで構成された Windows 表示言語で機能します。</span><span class="sxs-lookup"><span data-stu-id="b756a-112">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="b756a-113">また、サービス品質を最大限に高めるために、 **オンライン音声認識** を有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b756a-113">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Windows 音声認識の設定](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="b756a-115">アプリケーションが最初にマイクを有効にするかどうかを確認すると、ダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b756a-115">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="b756a-116">**[はい]** を選択すると、アプリで音声入力が開始されます。</span><span class="sxs-lookup"><span data-stu-id="b756a-116">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="b756a-117">音声入力には、特別な Windows Mixed Reality Api は必要ありません。これは、既存の Unreal Engine 4 [入力](https://docs.unrealengine.com/Gameplay/Input/index.html) マッピング API を基に構築されています。</span><span class="sxs-lookup"><span data-stu-id="b756a-117">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="b756a-118">音声マッピングの追加</span><span class="sxs-lookup"><span data-stu-id="b756a-118">Adding Speech Mappings</span></span>

<span data-ttu-id="b756a-119">音声入力を使用する場合は、音声をアクションに接続することが重要な手順です。</span><span class="sxs-lookup"><span data-stu-id="b756a-119">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="b756a-120">これらのマッピングは、ユーザーが話す可能性のある音声キーワードをアプリで監視し、リンクされたアクションを起動します。</span><span class="sxs-lookup"><span data-stu-id="b756a-120">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="b756a-121">音声マッピングは、次の方法で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="b756a-121">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="b756a-122">[ **プロジェクト設定の編集 >**] を選択し、[ **エンジン** ] セクションまでスクロールして [ **入力**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b756a-122">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="b756a-123">ジャンプコマンドの新しい音声マッピングを追加するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="b756a-123">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="b756a-124">[ **+** **配列要素** ] の横にあるアイコンを選択し、次の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="b756a-124">Select the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="b756a-125">**アクション名** の **jumpWord**</span><span class="sxs-lookup"><span data-stu-id="b756a-125">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="b756a-126">**Speech キーワード** の **ジャンプ**</span><span class="sxs-lookup"><span data-stu-id="b756a-126">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="b756a-127">すべての英語の単語または短い文をキーワードとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="b756a-127">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![UE4 Engine の入力設定](images/unreal/engine-input.png)

<span data-ttu-id="b756a-129">音声マッピングは、アクションや軸のマッピングなどの入力コンポーネントとして、またはイベントグラフのブループリントノードとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="b756a-129">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="b756a-130">たとえば、ジャンプコマンドをリンクして、単語が話されるタイミングに応じて2つの異なるログを出力することができます。</span><span class="sxs-lookup"><span data-stu-id="b756a-130">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="b756a-131">ブループリントをダブルクリックして、 **イベントグラフ** で開きます。</span><span class="sxs-lookup"><span data-stu-id="b756a-131">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="b756a-132">**右クリック** して音声マッピングの **アクション名** (この場合は **jumpWord**) を検索し、 **enter キー** を押して **入力アクション** ノードをグラフに追加します。</span><span class="sxs-lookup"><span data-stu-id="b756a-132">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter** to add an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="b756a-133">次の図に示すように、 **押さ** れた pin をドラッグアンドドロップして文字列ノードを **印刷** します。</span><span class="sxs-lookup"><span data-stu-id="b756a-133">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="b756a-134">**解放** された pin は空のままにすることができ、音声マッピングの場合は何も実行されません。</span><span class="sxs-lookup"><span data-stu-id="b756a-134">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![音声の単純なアクション](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="b756a-136">アプリを再生し、word の **ジャンプ** と言って、コンソールでログを出力します。</span><span class="sxs-lookup"><span data-stu-id="b756a-136">Play the app, say the word **jump**, and watch the console print out the logs!</span></span>

<span data-ttu-id="b756a-137">これで、HoloLens アプリへの音声入力の追加を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b756a-137">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="b756a-138">音声と対話機能の詳細については、以下のリンクを参照してください。ユーザー向けに作成しているエクスペリエンスについて考えてください。</span><span class="sxs-lookup"><span data-stu-id="b756a-138">You can find more information on speech and interactivity at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b756a-139">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="b756a-139">Next Development Checkpoint</span></span>

<span data-ttu-id="b756a-140">デプロイされていない実際の開発については、次に、Mixed Reality プラットフォームの機能と Api について説明します。</span><span class="sxs-lookup"><span data-stu-id="b756a-140">If you're following the Unreal development journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="b756a-141">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="b756a-141">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="b756a-142">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="b756a-142">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b756a-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="b756a-143">See also</span></span>
* [<span data-ttu-id="b756a-144">音声入力</span><span class="sxs-lookup"><span data-stu-id="b756a-144">Voice Input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="b756a-145">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="b756a-145">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="b756a-146">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="b756a-146">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)

