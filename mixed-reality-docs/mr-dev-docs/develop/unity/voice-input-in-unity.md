---
title: Unity の音声入力
description: Unity が Windows Mixed Reality アプリケーションに音声入力、音声認識、およびディクテーションを追加するための3つの方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 音声入力、KeywordRecognizer、GrammarRecognizer、マイク、ディクテーション、音声、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実ヘッドセット、MRTK、Mixed Reality ツールキット
ms.openlocfilehash: 7268a4df9c7fce03029937c72540ed274574067d
ms.sourcegitcommit: 8c3af63fb49494f75c8ab46236fc3dd8533c1e9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99606117"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="93d54-104">Unity の音声入力</span><span class="sxs-lookup"><span data-stu-id="93d54-104">Voice input in Unity</span></span>

> [!CAUTION]
> <span data-ttu-id="93d54-105">開始する前に、認識音声サービス SDK の Unity プラグインを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="93d54-105">Before starting, consider using the Unity plug-in for the Cognitive Speech Services SDK.</span></span> <span data-ttu-id="93d54-106">このプラグインを使用すると、音声からテキストへのデコードが簡単になります。また、ダイアログ、インテントベースの対話、翻訳、テキスト合成合成、自然言語音声認識などの高度な音声機能も利用できます。</span><span class="sxs-lookup"><span data-stu-id="93d54-106">The plugin has better Speech Accuracy results and easy access to speech-to-text decode, as well as advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis, and natural language speech recognition.</span></span> <span data-ttu-id="93d54-107">まず、 [サンプルとドキュメント](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="93d54-107">To get started, check out the [sample and documentation](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span></span>

<span data-ttu-id="93d54-108">Unity では、Unity アプリケーションに [音声入力](../../design/voice-input.md) を追加する3つの方法を公開しています。最初の2つは、PhraseRecognizer の種類です。</span><span class="sxs-lookup"><span data-stu-id="93d54-108">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application, the first two of which are types of PhraseRecognizer:</span></span>
* <span data-ttu-id="93d54-109">は、アプリに、 `KeywordRecognizer` リッスンする文字列コマンドの配列を提供します。</span><span class="sxs-lookup"><span data-stu-id="93d54-109">The `KeywordRecognizer` supplies your app with an array of string commands to listen for</span></span>
* <span data-ttu-id="93d54-110">は、 `GrammarRecognizer` アプリに、リッスンする特定の文法を定義する SRGS ファイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="93d54-110">The `GrammarRecognizer` gives your app an SRGS file defining a specific grammar to listen for</span></span>
* <span data-ttu-id="93d54-111">を使用する `DictationRecognizer` と、アプリは任意の単語をリッスンし、ユーザーに対してノートまたはその他の音声の表示を提供できます。</span><span class="sxs-lookup"><span data-stu-id="93d54-111">The `DictationRecognizer` lets your app listen for any word and provide the user with a note or other display of their speech</span></span>

> [!NOTE]
> <span data-ttu-id="93d54-112">ディクテーションと語句の認識を同時に処理することはできません。</span><span class="sxs-lookup"><span data-stu-id="93d54-112">Dictation and phrase recognition can't be handled at the same time.</span></span> <span data-ttu-id="93d54-113">GrammarRecognizer または KeywordRecognizer がアクティブである場合、DictationRecognizer をアクティブにすることはできず、その逆も可能です。</span><span class="sxs-lookup"><span data-stu-id="93d54-113">If a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can't be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="93d54-114">音声用の機能を有効にする</span><span class="sxs-lookup"><span data-stu-id="93d54-114">Enabling the capability for Voice</span></span>

<span data-ttu-id="93d54-115">音声入力を使用するアプリの **マイク** 機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93d54-115">The **Microphone** capability must be declared for an app to use Voice input.</span></span>
1. <span data-ttu-id="93d54-116">Unity エディターで、[ **Edit > Project Settings > Player** ] に移動します。</span><span class="sxs-lookup"><span data-stu-id="93d54-116">In the Unity Editor, navigate to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="93d54-117">[ **Windows ストア** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="93d54-117">Select the **Windows Store** tab</span></span>
3. <span data-ttu-id="93d54-118">[ **発行の設定 > 機能** ] セクションで、 **マイク** の機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="93d54-118">In the **Publishing Settings > Capabilities** section, check the **Microphone** capability</span></span>
4. <span data-ttu-id="93d54-119">HoloLens デバイスでマイクにアクセスするためのアクセス許可をアプリに付与する</span><span class="sxs-lookup"><span data-stu-id="93d54-119">Grant permissions to the app for microphone access on your HoloLens device</span></span>
    * <span data-ttu-id="93d54-120">デバイスの起動時にこれを行うように求められますが、誤って [いいえ] をクリックした場合は、デバイスの設定でアクセス許可を変更できます。</span><span class="sxs-lookup"><span data-stu-id="93d54-120">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="93d54-121">フレーズ認識</span><span class="sxs-lookup"><span data-stu-id="93d54-121">Phrase Recognition</span></span>

<span data-ttu-id="93d54-122">ユーザーによって読み上げられた特定の語句をアプリでリッスンできるようにするには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="93d54-122">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="93d54-123">またはを使用してリッスンする語句を指定します `KeywordRecognizer``GrammarRecognizer`</span><span class="sxs-lookup"><span data-stu-id="93d54-123">Specify which phrases to listen for using a `KeywordRecognizer` or `GrammarRecognizer`</span></span>
2. <span data-ttu-id="93d54-124">イベントを処理 `OnPhraseRecognized` し、認識された語句に対応するアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="93d54-124">Handle the `OnPhraseRecognized` event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="93d54-125">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="93d54-125">KeywordRecognizer</span></span>

<span data-ttu-id="93d54-126">**名前空間:** *Unityengine。 Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="93d54-126">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="93d54-127">**型:** *KeywordRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="93d54-127">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="93d54-128">一部のキーストロークを保存するには、いくつかの using ステートメントが必要です。</span><span class="sxs-lookup"><span data-stu-id="93d54-128">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="93d54-129">次に、クラスにいくつかのフィールドを追加して、レコグナイザーとキーワード >アクションディクショナリを格納します。</span><span class="sxs-lookup"><span data-stu-id="93d54-129">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="93d54-130">次に、メソッドのなど、辞書にキーワードを追加 `Start()` します。</span><span class="sxs-lookup"><span data-stu-id="93d54-130">Now add a keyword to the dictionary, for example in of a `Start()` method.</span></span> <span data-ttu-id="93d54-131">この例では、"activate" キーワードを追加しています。</span><span class="sxs-lookup"><span data-stu-id="93d54-131">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="93d54-132">キーワードレコグナイザーを作成し、認識する内容を指定します。</span><span class="sxs-lookup"><span data-stu-id="93d54-132">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="93d54-133">ここでイベントに登録します `OnPhraseRecognized`</span><span class="sxs-lookup"><span data-stu-id="93d54-133">Now register for the `OnPhraseRecognized` event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="93d54-134">ハンドラーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="93d54-134">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="93d54-135">最後に、認識を開始します。</span><span class="sxs-lookup"><span data-stu-id="93d54-135">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="93d54-136">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="93d54-136">GrammarRecognizer</span></span>

<span data-ttu-id="93d54-137">**名前空間:** *Unityengine。 Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="93d54-137">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="93d54-138">**型**: *GrammarRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="93d54-138">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="93d54-139">GrammarRecognizer は、SRGS を使用して認識文法を指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="93d54-139">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="93d54-140">これは、アプリにいくつかのキーワードしか含まれていない場合、より複雑な語句を認識する場合、またはコマンドのセットを簡単にオン/オフにする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="93d54-140">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="93d54-141">詳細については、「 [SRGS XML を使用して](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) ファイル形式情報を作成する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93d54-141">See: [Create Grammars Using SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) for file format information.</span></span>

<span data-ttu-id="93d54-142">SRGS 文法を取得し、それがプロジェクト内の [Streamingassets フォルダー](https://docs.unity3d.com/Manual/StreamingAssets.html)にある場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="93d54-142">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="93d54-143">を作成 `GrammarRecognizer` し、SRGS ファイルへのパスを渡します。</span><span class="sxs-lookup"><span data-stu-id="93d54-143">Create a `GrammarRecognizer` and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="93d54-144">ここでイベントに登録します `OnPhraseRecognized`</span><span class="sxs-lookup"><span data-stu-id="93d54-144">Now register for the `OnPhraseRecognized` event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="93d54-145">SRGS 文法に指定されている情報を含むコールバックが取得されます。これは適切に処理できます。</span><span class="sxs-lookup"><span data-stu-id="93d54-145">You'll get a callback containing information specified in your SRGS grammar, which you can handle appropriately.</span></span> <span data-ttu-id="93d54-146">重要な情報の大部分は配列で提供され `semanticMeanings` ます。</span><span class="sxs-lookup"><span data-stu-id="93d54-146">Most of the important information will be provided in the `semanticMeanings` array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="93d54-147">最後に、認識を開始します。</span><span class="sxs-lookup"><span data-stu-id="93d54-147">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="93d54-148">ディクテーション</span><span class="sxs-lookup"><span data-stu-id="93d54-148">Dictation</span></span>

<span data-ttu-id="93d54-149">**名前空間:** *Unityengine。 Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="93d54-149">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="93d54-150">**型**: *DictationRecognizer*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="93d54-150">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="93d54-151">を使用して、 `DictationRecognizer` ユーザーの音声をテキストに変換します。</span><span class="sxs-lookup"><span data-stu-id="93d54-151">Use the `DictationRecognizer` to convert the user's speech to text.</span></span> <span data-ttu-id="93d54-152">DictationRecognizer は [ディクテーション](../../design/voice-input.md#dictation) 機能を公開しており、仮説と語句の完了イベントの登録とリッスンをサポートしているので、ユーザーが話すときと後の両方でユーザーにフィードバックを提供できます。</span><span class="sxs-lookup"><span data-stu-id="93d54-152">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="93d54-153">`Start()` および `Stop()` メソッドは、それぞれディクテーション認識を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="93d54-153">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="93d54-154">レコグナイザーを使用したら、を使用して破棄し、使用するリソースを解放する必要があり `Dispose()` ます。</span><span class="sxs-lookup"><span data-stu-id="93d54-154">Once done with the recognizer, it should be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="93d54-155">これらのリソースは、その前にリリースされていない場合、追加のパフォーマンスコストで、ガベージコレクション中に自動的に解放されます。</span><span class="sxs-lookup"><span data-stu-id="93d54-155">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>

<span data-ttu-id="93d54-156">ディクテーションを開始するには、いくつかの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93d54-156">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="93d54-157">新しいを作成する `DictationRecognizer`</span><span class="sxs-lookup"><span data-stu-id="93d54-157">Create a new `DictationRecognizer`</span></span>
2. <span data-ttu-id="93d54-158">ディクテーションイベントの処理</span><span class="sxs-lookup"><span data-stu-id="93d54-158">Handle Dictation events</span></span>
3. <span data-ttu-id="93d54-159">DictationRecognizer を開始する</span><span class="sxs-lookup"><span data-stu-id="93d54-159">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="93d54-160">ディクテーション用の機能を有効にする</span><span class="sxs-lookup"><span data-stu-id="93d54-160">Enabling the capability for dictation</span></span>

<span data-ttu-id="93d54-161">音声認識を使用するには、 **インターネットクライアント** と **マイク** の機能を次のように宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93d54-161">The **Internet Client** and **Microphone** capabilities must be declared for an app to use dictation:</span></span>
1. <span data-ttu-id="93d54-162">Unity エディターで、[ **Edit > Project Settings > Player** ] を開きます。</span><span class="sxs-lookup"><span data-stu-id="93d54-162">In the Unity Editor, go to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="93d54-163">[ **Windows ストア** ] タブで、を選択します。</span><span class="sxs-lookup"><span data-stu-id="93d54-163">Select on the **Windows Store** tab</span></span>
3. <span data-ttu-id="93d54-164">[ **発行の設定 > 機能** ] セクションで、 **internetclient** の機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="93d54-164">In the **Publishing Settings > Capabilities** section, check the **InternetClient** capability</span></span>
    * <span data-ttu-id="93d54-165">マイクをまだ有効にしていない場合は、必要に応じて **マイク** の機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="93d54-165">Optionally, if you didn't already enable the microphone, check the **Microphone** capability</span></span>
4. <span data-ttu-id="93d54-166">HoloLens デバイスでマイクアクセスを行うためのアクセス許可をアプリに付与します (まだインストールしていない場合)。</span><span class="sxs-lookup"><span data-stu-id="93d54-166">Grant permissions to the app for microphone access on your HoloLens device if you haven't already</span></span>
    * <span data-ttu-id="93d54-167">デバイスの起動時にこれを行うように求められますが、誤って [いいえ] をクリックした場合は、デバイスの設定でアクセス許可を変更できます。</span><span class="sxs-lookup"><span data-stu-id="93d54-167">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="93d54-168">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="93d54-168">DictationRecognizer</span></span>

<span data-ttu-id="93d54-169">次のような DictationRecognizer を作成します。</span><span class="sxs-lookup"><span data-stu-id="93d54-169">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="93d54-170">ディクテーションの動作を実装するためにサブスクライブおよび処理できるディクテーションイベントは4つあります。</span><span class="sxs-lookup"><span data-stu-id="93d54-170">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

<span data-ttu-id="93d54-171">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="93d54-171">**DictationResult**</span></span>

<span data-ttu-id="93d54-172">このイベントは、ユーザーが一時停止した後、通常は文の最後に発生します。</span><span class="sxs-lookup"><span data-stu-id="93d54-172">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="93d54-173">完全に認識された文字列がここに返されます。</span><span class="sxs-lookup"><span data-stu-id="93d54-173">The full recognized string is returned here.</span></span>

<span data-ttu-id="93d54-174">まず、イベントをサブスクライブし `DictationResult` ます。</span><span class="sxs-lookup"><span data-stu-id="93d54-174">First, subscribe to the `DictationResult` event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="93d54-175">次に、DictationResult コールバックを処理します。</span><span class="sxs-lookup"><span data-stu-id="93d54-175">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="93d54-176">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="93d54-176">**DictationHypothesis**</span></span>

<span data-ttu-id="93d54-177">このイベントは、ユーザーが話している間、継続的に発生します。</span><span class="sxs-lookup"><span data-stu-id="93d54-177">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="93d54-178">認識エンジンがリッスンすると、これまでに知られている内容のテキストが提供されます。</span><span class="sxs-lookup"><span data-stu-id="93d54-178">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="93d54-179">まず、イベントをサブスクライブし `DictationHypothesis` ます。</span><span class="sxs-lookup"><span data-stu-id="93d54-179">First, subscribe to the `DictationHypothesis` event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="93d54-180">次に、DictationHypothesis コールバックを処理します。</span><span class="sxs-lookup"><span data-stu-id="93d54-180">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="93d54-181">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="93d54-181">**DictationComplete**</span></span>

<span data-ttu-id="93d54-182">このイベントは、レコグナイザー () が呼び出されているか、タイムアウトが発生したか、またはその他のエラーが発生した場合に、レコグナイザーが停止したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="93d54-182">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="93d54-183">まず、イベントをサブスクライブし `DictationComplete` ます。</span><span class="sxs-lookup"><span data-stu-id="93d54-183">First, subscribe to the `DictationComplete` event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="93d54-184">次に、DictationComplete コールバックを処理します。</span><span class="sxs-lookup"><span data-stu-id="93d54-184">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="93d54-185">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="93d54-185">**DictationError**</span></span>

<span data-ttu-id="93d54-186">このイベントは、エラーが発生したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="93d54-186">This event is fired when an error occurs.</span></span>

<span data-ttu-id="93d54-187">まず、イベントをサブスクライブし `DictationError` ます。</span><span class="sxs-lookup"><span data-stu-id="93d54-187">First, subscribe to the `DictationError` event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="93d54-188">次に、DictationError コールバックを処理します。</span><span class="sxs-lookup"><span data-stu-id="93d54-188">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="93d54-189">使用するディクテーションイベントをサブスクライブして処理したら、ディクテーションエンジンを起動してイベントの受信を開始します。</span><span class="sxs-lookup"><span data-stu-id="93d54-189">Once you've subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="93d54-190">DictationRecognizer を維持する必要がなくなった場合は、イベントのサブスクリプションを解除し、DictationRecognizer を破棄する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93d54-190">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="93d54-191">**ヒント**</span><span class="sxs-lookup"><span data-stu-id="93d54-191">**Tips**</span></span>
* <span data-ttu-id="93d54-192">`Start()` および `Stop()` メソッドは、それぞれディクテーション認識を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="93d54-192">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="93d54-193">認識エンジンが完成したら、を使用してそのレコグナイザーを破棄し、使用するリソースを解放する必要があり `Dispose()` ます。</span><span class="sxs-lookup"><span data-stu-id="93d54-193">Once done with the recognizer, it must be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="93d54-194">これらのリソースは、その前にリリースされていない場合、追加のパフォーマンスコストで、ガベージコレクション中に自動的に解放されます。</span><span class="sxs-lookup"><span data-stu-id="93d54-194">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>
* <span data-ttu-id="93d54-195">タイムアウトは、一定の時間が経過すると発生します。</span><span class="sxs-lookup"><span data-stu-id="93d54-195">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="93d54-196">これらのタイムアウトは、イベントで確認でき `DictationComplete` ます。</span><span class="sxs-lookup"><span data-stu-id="93d54-196">You can check for these timeouts in the `DictationComplete` event.</span></span> <span data-ttu-id="93d54-197">次の2つの点に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93d54-197">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="93d54-198">認識エンジンが起動し、最初の5秒間オーディオが聞こえない場合は、タイムアウトになります。</span><span class="sxs-lookup"><span data-stu-id="93d54-198">If the recognizer starts and doesn't hear any audio for the first five seconds, it will time out.</span></span>
   2. <span data-ttu-id="93d54-199">認識エンジンから結果が得られたが、20秒間、無音が聞こえた場合、タイムアウトになります。</span><span class="sxs-lookup"><span data-stu-id="93d54-199">If the recognizer has given a result, but then hears silence for 20 seconds, it will time out.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="93d54-200">語句認識とディクテーションの両方を使用する</span><span class="sxs-lookup"><span data-stu-id="93d54-200">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="93d54-201">アプリでフレーズ認識とディクテーションの両方を使用する場合は、もう一方を開始する前に、1つを完全にシャットダウンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="93d54-201">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="93d54-202">複数の KeywordRecognizers を実行している場合は、次のようにして一度にシャットダウンできます。</span><span class="sxs-lookup"><span data-stu-id="93d54-202">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="93d54-203">`Restart()`を呼び出して、DictationRecognizer が停止した後、すべてのレコグナイザーを前の状態に復元することができます。</span><span class="sxs-lookup"><span data-stu-id="93d54-203">You can call `Restart()` to restore all recognizers to their previous state after the DictationRecognizer has stopped:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="93d54-204">KeywordRecognizer を開始することもできます。これにより、PhraseRecognitionSystem も再起動されます。</span><span class="sxs-lookup"><span data-stu-id="93d54-204">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="93d54-205">混合 Reality ツールキットでの音声入力</span><span class="sxs-lookup"><span data-stu-id="93d54-205">Voice input in Mixed Reality Toolkit</span></span>

<span data-ttu-id="93d54-206">音声入力の MRTK の例については、次のデモシーンをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="93d54-206">You can find MRTK examples for voice input in the following demo scenes:</span></span>
* [<span data-ttu-id="93d54-207">ディクテーション</span><span class="sxs-lookup"><span data-stu-id="93d54-207">Dictation</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [<span data-ttu-id="93d54-208">Speech</span><span class="sxs-lookup"><span data-stu-id="93d54-208">Speech</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a><span data-ttu-id="93d54-209">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="93d54-209">Next Development Checkpoint</span></span>

<span data-ttu-id="93d54-210">ここまでに説明した Unity 開発チェックポイントの旅に従っている場合、次のタスクでは、Mixed Reality プラットフォームの機能と Api について説明します。</span><span class="sxs-lookup"><span data-stu-id="93d54-210">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="93d54-211">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="93d54-211">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="93d54-212">いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="93d54-212">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>