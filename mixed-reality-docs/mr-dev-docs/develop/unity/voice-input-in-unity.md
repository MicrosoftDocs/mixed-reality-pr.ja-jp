---
title: Unity の音声入力
description: Unity では、Windows Mixed Reality アプリケーションに音声入力を追加する3つの方法が公開されています。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 音声入力、KeywordRecognizer、GrammarRecognizer、マイク、ディクテーション、音声
ms.openlocfilehash: b6930b35046e32beb1a4ca9f9ca29996487fcf4d
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687250"
---
# <a name="voice-input-in-unity"></a>Unity の音声入力

>[!NOTE]
>以下の情報の代わりに、認識音声サービス SDK の Unity プラグインを使用することを検討してください。これにより、音声の精度が大幅に向上します。また、音声からテキストへのデコードや、ダイアログ、インテントベースの対話、翻訳、テキスト合成合成、自然言語音声認識などの高度な音声機能に簡単にアクセスできます。 ここでサンプルとドキュメントを見つけます。 https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity   

Unity では、Unity アプリケーションに [音声入力](../../design/voice-input.md) を追加する3つの方法が公開されています。

KeywordRecognizer (2 種類の PhraseRecognizers のいずれか) では、アプリには、リッスンする文字列コマンドの配列を指定できます。 GrammarRecognizer (他の種類の PhraseRecognizer) では、リッスンする特定の文法を定義する SRGS ファイルをアプリに与えることができます。 DictationRecognizer を使用すると、アプリは任意の単語をリッスンし、ユーザーにノートやその他の音声の表示を提供できます。

>[!NOTE]
>ディクテーションまたはフレーズ認識だけを一度に処理できます。 つまり、GrammarRecognizer または KeywordRecognizer がアクティブである場合、DictationRecognizer をアクティブにすることはできず、その逆も可能です。

## <a name="enabling-the-capability-for-voice"></a>音声用の機能を有効にする

音声入力を利用するには、 **マイク** の機能がアプリに対して宣言されている必要があります。
1. Unity エディターで、[Edit > Project Settings > Player] の順に移動して、windows media player の設定に移動します。
2. [Windows ストア] タブをクリックします。
3. [発行設定 > 機能] セクションで、 **マイク** の機能を確認します。

## <a name="phrase-recognition"></a>フレーズ認識

ユーザーによって読み上げられた特定の語句をアプリでリッスンできるようにするには、次の操作を行う必要があります。
1. KeywordRecognizer または GrammarRecognizer を使用してリッスンする語句を指定します
2. OnPhraseRecognized イベントを処理し、認識された語句に対応するアクションを実行します。

### <a name="keywordrecognizer"></a>KeywordRecognizer

**名前空間:** *Unityengine。 Windows. Speech*<br>
**型:** *KeywordRecognizer* 、 *PhraseRecognizedEventArgs* 、 *SpeechError* 、 *SpeechSystemStatus*

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

次に、キーワードを辞書に追加します (Start () メソッドの内部など)。 この例では、"activate" キーワードを追加しています。

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

次に、OnPhraseRecognized イベントに登録します。

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
**型** : *GrammarRecognizer* 、 *PhraseRecognizedEventArgs* 、 *SpeechError* 、 *SpeechSystemStatus*

GrammarRecognizer は、SRGS を使用して認識文法を指定する場合に使用します。 これは、アプリにいくつかのキーワードしか含まれていない場合、より複雑な語句を認識する場合、またはコマンドのセットを簡単にオン/オフにする場合に便利です。 詳細については、「 [SRGS XML を使用して](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) ファイル形式情報を作成する」を参照してください。

SRGS 文法を取得し、それがプロジェクト内の [Streamingassets フォルダー](https://docs.unity3d.com/Manual/StreamingAssets.html)にある場合は、次のようになります。

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

GrammarRecognizer を作成し、SRGS ファイルへのパスを渡します。

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

次に、OnPhraseRecognized イベントに登録します。

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

必要に応じて処理できる、SRGS 文法に指定されている情報を含むコールバックが取得されます。 重要な情報の大部分は、semanticMeanings 配列に記載されています。

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
**型** : *DictationRecognizer* 、 *SpeechError* 、 *SpeechSystemStatus*

DictationRecognizer を使用して、ユーザーの音声をテキストに変換します。 DictationRecognizer は [ディクテーション](../../design/voice-input.md#dictation) 機能を公開しており、仮説と語句の完了イベントの登録とリッスンをサポートしているので、ユーザーが話すときと後の両方でユーザーにフィードバックを提供できます。 Start () メソッドと Stop () メソッドは、それぞれディクテーション認識を有効または無効にします。 レコグナイザーを使用したら、Dispose () メソッドを使用して破棄し、使用するリソースを解放する必要があります。 これらのリソースは、それより前にリリースされていない場合、追加のパフォーマンスコストで、ガベージコレクション中に自動的に解放されます。

ディクテーションを開始するには、いくつかの手順を実行する必要があります。
1. 新しい DictationRecognizer を作成する
2. ディクテーションイベントの処理
3. DictationRecognizer を開始する

### <a name="enabling-the-capability-for-dictation"></a>ディクテーション用の機能を有効にする

"インターネットクライアント" 機能は、前述の "マイク" 機能に加えて、ディクテーションを利用するためにアプリに対して宣言されている必要があります。
1. Unity エディターで、[Edit > Project Settings > Player] ページに移動して、windows media player の設定に移動します。
2. [Windows ストア] タブをクリックします。
3. [発行の設定 > 機能] セクションで、 **Internetclient** の機能を確認します。

### <a name="dictationrecognizer"></a>DictationRecognizer

次のような DictationRecognizer を作成します。

```
dictationRecognizer = new DictationRecognizer();
```

ディクテーションの動作を実装するためにサブスクライブおよび処理できるディクテーションイベントは4つあります。
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

このイベントは、ユーザーが一時停止した後、通常は文の最後に発生します。 完全に認識された文字列がここに返されます。

まず、DictationResult イベントをサブスクライブします。

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

まず、DictationHypothesis イベントをサブスクライブします。

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

まず、DictationComplete イベントをサブスクライブします。

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

まず、DictationError イベントをサブスクライブします。

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
* Start () メソッドと Stop () メソッドは、それぞれディクテーション認識を有効または無効にします。
* レコグナイザーを使用したら、Dispose () メソッドを使用して破棄し、使用するリソースを解放する必要があります。 これらのリソースは、それより前にリリースされていない場合、追加のパフォーマンスコストで、ガベージコレクション中に自動的に解放されます。
* タイムアウトは、一定の時間が経過すると発生します。 これらのタイムアウトは、DictationComplete イベントで確認できます。 次の2つの点に注意する必要があります。
   1. 認識エンジンが起動し、最初の5秒間オーディオが聞こえない場合は、タイムアウトします。
   2. 認識エンジンが結果を指定した後、20秒間無音の状態になると、タイムアウトします。

## <a name="using-both-phrase-recognition-and-dictation"></a>語句認識とディクテーションの両方を使用する

アプリでフレーズ認識とディクテーションの両方を使用する場合は、もう一方を開始する前に、1つを完全にシャットダウンする必要があります。 複数の KeywordRecognizers を実行している場合は、次のようにして一度にシャットダウンできます。

```
PhraseRecognitionSystem.Shutdown();
```

すべてのレコグナイザーを前の状態に復元するには、DictationRecognizer が停止した後、次のように呼び出します。

```
PhraseRecognitionSystem.Restart();
```

KeywordRecognizer を開始することもできます。これにより、PhraseRecognitionSystem も再起動されます。

## <a name="using-the-microphone-helper"></a>マイクヘルパーの使用

GitHub の Mixed Reality Toolkit には、システムに使用可能なマイクがある場合に開発者にヒントを表示するマイクヘルパークラスが含まれています。 ここでの用途の1つは、システム上にマイクがあるかどうかを確認してから、アプリケーションで音声操作のヒントを表示することです。

マイクヘルパースクリプトは、[ [入力/スクリプト/ユーティリティ] フォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)にあります。 GitHub リポジトリには、ヘルパーの使用方法を示す [小さなサンプル](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) も含まれています。

## <a name="voice-input-in-mixed-reality-toolkit"></a>混合 Reality ツールキットでの音声入力
このシーンでは、音声入力の例を確認できます。

- [HoloToolkit-Examples/Input/シーン/SpeechInputSource](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)

## <a name="next-development-checkpoint"></a>次回の開発チェックポイント

ここまでに説明した Unity 開発チェックポイントの旅に従っている場合、次のタスクでは、Mixed Reality プラットフォームの機能と Api について説明します。

> [!div class="nextstepaction"]
> [共有エクスペリエンス](shared-experiences-in-unity.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks) に戻ることができます。
