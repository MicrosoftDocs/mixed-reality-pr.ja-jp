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
# <a name="voice-input-in-unity"></a>Unity の音声入力

> [!CAUTION]
> 開始する前に、認識音声サービス SDK の Unity プラグインを使用することを検討してください。 このプラグインを使用すると、音声からテキストへのデコードが簡単になります。また、ダイアログ、インテントベースの対話、翻訳、テキスト合成合成、自然言語音声認識などの高度な音声機能も利用できます。 まず、 [サンプルとドキュメント](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity)を確認してください。

Unity では、Unity アプリケーションに [音声入力](../../design/voice-input.md) を追加する3つの方法を公開しています。最初の2つは、PhraseRecognizer の種類です。
* は、アプリに、 `KeywordRecognizer` リッスンする文字列コマンドの配列を提供します。
* は、 `GrammarRecognizer` アプリに、リッスンする特定の文法を定義する SRGS ファイルを提供します。
* を使用する `DictationRecognizer` と、アプリは任意の単語をリッスンし、ユーザーに対してノートまたはその他の音声の表示を提供できます。

> [!NOTE]
> ディクテーションと語句の認識を同時に処理することはできません。 GrammarRecognizer または KeywordRecognizer がアクティブである場合、DictationRecognizer をアクティブにすることはできず、その逆も可能です。

## <a name="enabling-the-capability-for-voice"></a>音声用の機能を有効にする

音声入力を使用するアプリの **マイク** 機能を宣言する必要があります。
1. Unity エディターで、[ **Edit > Project Settings > Player** ] に移動します。
2. [ **Windows ストア** ] タブを選択します。
3. [ **発行の設定 > 機能** ] セクションで、 **マイク** の機能を確認します。
4. HoloLens デバイスでマイクにアクセスするためのアクセス許可をアプリに付与する
    * デバイスの起動時にこれを行うように求められますが、誤って [いいえ] をクリックした場合は、デバイスの設定でアクセス許可を変更できます。

## <a name="phrase-recognition"></a>フレーズ認識

ユーザーによって読み上げられた特定の語句をアプリでリッスンできるようにするには、次の操作を行う必要があります。
1. またはを使用してリッスンする語句を指定します `KeywordRecognizer``GrammarRecognizer`
2. イベントを処理 `OnPhraseRecognized` し、認識された語句に対応するアクションを実行します。

### <a name="keywordrecognizer"></a>KeywordRecognizer

**名前空間:** *Unityengine。 Windows. Speech*<br>
**型:** *KeywordRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*

一部のキーストロークを保存するには、いくつかの using ステートメントが必要です。

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

次に、クラスにいくつかのフィールドを追加して、レコグナイザーとキーワード >アクションディクショナリを格納します。

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

次に、メソッドのなど、辞書にキーワードを追加 `Start()` します。 この例では、"activate" キーワードを追加しています。

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

キーワードレコグナイザーを作成し、認識する内容を指定します。

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

ここでイベントに登録します `OnPhraseRecognized`

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

ハンドラーの例を次に示します。

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

最後に、認識を開始します。

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**名前空間:** *Unityengine。 Windows. Speech*<br>
**型**: *GrammarRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*

GrammarRecognizer は、SRGS を使用して認識文法を指定する場合に使用します。 これは、アプリにいくつかのキーワードしか含まれていない場合、より複雑な語句を認識する場合、またはコマンドのセットを簡単にオン/オフにする場合に便利です。 詳細については、「 [SRGS XML を使用して](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) ファイル形式情報を作成する」を参照してください。

SRGS 文法を取得し、それがプロジェクト内の [Streamingassets フォルダー](https://docs.unity3d.com/Manual/StreamingAssets.html)にある場合は、次のようになります。

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

を作成 `GrammarRecognizer` し、SRGS ファイルへのパスを渡します。

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

ここでイベントに登録します `OnPhraseRecognized`

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

SRGS 文法に指定されている情報を含むコールバックが取得されます。これは適切に処理できます。 重要な情報の大部分は配列で提供され `semanticMeanings` ます。

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

最後に、認識を開始します。

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>ディクテーション

**名前空間:** *Unityengine。 Windows. Speech*<br>
**型**: *DictationRecognizer*、 *SpeechError*、 *SpeechSystemStatus*

を使用して、 `DictationRecognizer` ユーザーの音声をテキストに変換します。 DictationRecognizer は [ディクテーション](../../design/voice-input.md#dictation) 機能を公開しており、仮説と語句の完了イベントの登録とリッスンをサポートしているので、ユーザーが話すときと後の両方でユーザーにフィードバックを提供できます。 `Start()` および `Stop()` メソッドは、それぞれディクテーション認識を有効または無効にします。 レコグナイザーを使用したら、を使用して破棄し、使用するリソースを解放する必要があり `Dispose()` ます。 これらのリソースは、その前にリリースされていない場合、追加のパフォーマンスコストで、ガベージコレクション中に自動的に解放されます。

ディクテーションを開始するには、いくつかの手順を実行する必要があります。
1. 新しいを作成する `DictationRecognizer`
2. ディクテーションイベントの処理
3. DictationRecognizer を開始する

### <a name="enabling-the-capability-for-dictation"></a>ディクテーション用の機能を有効にする

音声認識を使用するには、 **インターネットクライアント** と **マイク** の機能を次のように宣言する必要があります。
1. Unity エディターで、[ **Edit > Project Settings > Player** ] を開きます。
2. [ **Windows ストア** ] タブで、を選択します。
3. [ **発行の設定 > 機能** ] セクションで、 **internetclient** の機能を確認します。
    * マイクをまだ有効にしていない場合は、必要に応じて **マイク** の機能を確認します。
4. HoloLens デバイスでマイクアクセスを行うためのアクセス許可をアプリに付与します (まだインストールしていない場合)。
    * デバイスの起動時にこれを行うように求められますが、誤って [いいえ] をクリックした場合は、デバイスの設定でアクセス許可を変更できます。

### <a name="dictationrecognizer"></a>DictationRecognizer

次のような DictationRecognizer を作成します。

```
dictationRecognizer = new DictationRecognizer();
```

ディクテーションの動作を実装するためにサブスクライブおよび処理できるディクテーションイベントは4つあります。
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

**DictationResult**

このイベントは、ユーザーが一時停止した後、通常は文の最後に発生します。 完全に認識された文字列がここに返されます。

まず、イベントをサブスクライブし `DictationResult` ます。

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

次に、DictationResult コールバックを処理します。

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

このイベントは、ユーザーが話している間、継続的に発生します。 認識エンジンがリッスンすると、これまでに知られている内容のテキストが提供されます。

まず、イベントをサブスクライブし `DictationHypothesis` ます。

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

次に、DictationHypothesis コールバックを処理します。

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

このイベントは、レコグナイザー () が呼び出されているか、タイムアウトが発生したか、またはその他のエラーが発生した場合に、レコグナイザーが停止したときに発生します。

まず、イベントをサブスクライブし `DictationComplete` ます。

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

次に、DictationComplete コールバックを処理します。

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

このイベントは、エラーが発生したときに発生します。

まず、イベントをサブスクライブし `DictationError` ます。

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

次に、DictationError コールバックを処理します。

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

使用するディクテーションイベントをサブスクライブして処理したら、ディクテーションエンジンを起動してイベントの受信を開始します。

```
dictationRecognizer.Start();
```

DictationRecognizer を維持する必要がなくなった場合は、イベントのサブスクリプションを解除し、DictationRecognizer を破棄する必要があります。

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**ヒント**
* `Start()` および `Stop()` メソッドは、それぞれディクテーション認識を有効または無効にします。
* 認識エンジンが完成したら、を使用してそのレコグナイザーを破棄し、使用するリソースを解放する必要があり `Dispose()` ます。 これらのリソースは、その前にリリースされていない場合、追加のパフォーマンスコストで、ガベージコレクション中に自動的に解放されます。
* タイムアウトは、一定の時間が経過すると発生します。 これらのタイムアウトは、イベントで確認でき `DictationComplete` ます。 次の2つの点に注意する必要があります。
   1. 認識エンジンが起動し、最初の5秒間オーディオが聞こえない場合は、タイムアウトになります。
   2. 認識エンジンから結果が得られたが、20秒間、無音が聞こえた場合、タイムアウトになります。

## <a name="using-both-phrase-recognition-and-dictation"></a>語句認識とディクテーションの両方を使用する

アプリでフレーズ認識とディクテーションの両方を使用する場合は、もう一方を開始する前に、1つを完全にシャットダウンする必要があります。 複数の KeywordRecognizers を実行している場合は、次のようにして一度にシャットダウンできます。

```
PhraseRecognitionSystem.Shutdown();
```

`Restart()`を呼び出して、DictationRecognizer が停止した後、すべてのレコグナイザーを前の状態に復元することができます。

```
PhraseRecognitionSystem.Restart();
```

KeywordRecognizer を開始することもできます。これにより、PhraseRecognitionSystem も再起動されます。

## <a name="voice-input-in-mixed-reality-toolkit"></a>混合 Reality ツールキットでの音声入力

音声入力の MRTK の例については、次のデモシーンをご覧ください。
* [ディクテーション](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [Speech](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

ここまでに説明した Unity 開発チェックポイントの旅に従っている場合、次のタスクでは、Mixed Reality プラットフォームの機能と Api について説明します。

> [!div class="nextstepaction"]
> [共有エクスペリエンス](shared-experiences-in-unity.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。