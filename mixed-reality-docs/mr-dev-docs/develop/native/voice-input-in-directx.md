---
title: DirectX の音声入力
description: Windows Mixed Reality の DirectX アプリで音声コマンドと小さなフレーズと文の認識を実装する方法について説明します。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: チュートリアル、音声コマンド、語句、認識、音声、directx、プラットフォーム、cortana、windows mixed reality
ms.openlocfilehash: 5f7ed587b474d147c0b13e4896a89f655f8dc30b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583741"
---
# <a name="voice-input-in-directx"></a>DirectX の音声入力

> [!NOTE]
> この記事は、従来の WinRT ネイティブ Api に関連しています。  新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](openxr-getting-started.md)** を使用することをお勧めします。

この記事では、Windows Mixed Reality の DirectX アプリで [音声コマンド](../../design/voice-input.md) と小さな語句と文認識を実装する方法について説明します。

>[!NOTE]
>この記事のコードスニペットは、 [C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用される c + c++ 17 準拠の c++/WinRT ではなく、c++/cx を使用します。  概念は C++/WinRT プロジェクトに相当しますが、コードを変換する必要があります。

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a>SpeechRecognizer を使用して音声認識を継続する

このセクションでは、音声認識を使用してアプリで音声コマンドを有効にする方法について説明します。 このチュートリアルでは、 [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) サンプルのコードを使用します。 サンプルを実行している場合は、登録されているいずれかのカラーコマンドの名前を読み上げて、回転しているキューブの色を変更します。

最初に、新しい *Windows:: Media:: SpeechRecognition:: SpeechRecognizer* インスタンスを作成します。

*HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState* から:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

レコグナイザーがリッスンする音声コマンドのリストを作成します。 ここでは、ホログラムの色を変更するための一連のコマンドを作成します。 便宜上、後でコマンドに使用するデータも作成します。

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

辞書に含まれていない可能性のある発音語を使用して、コマンドを指定できます。

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

Speech レコグナイザーの制約の一覧にコマンドリストを読み込むには、 [SpeechRecognitionListConstraint](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint) オブジェクトを使用します。

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

音声認識エンジンの[SpeechContinuousRecognitionSession](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession)で[resultgenerated](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession)イベントをサブスクライブします。 このイベントは、いずれかのコマンドが認識されたときにアプリに通知します。

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

*Onresultgenerated* イベントハンドラーは、 [SpeechContinuousRecognitionResultGeneratedEventArgs](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionResultGeneratedEventArgs)インスタンス内のイベントデータを受信します。 確信度が定義したしきい値を超える場合、アプリはイベントが発生したことを確認する必要があります。 後の更新ループで使用できるように、イベントデータを保存します。

*HolographicVoiceInputSampleMain* から:

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

このコード例では、ユーザーのコマンドに従って、回転したホログラムキューブの色を変更します。

*HolographicVoiceInputSampleMain:: Update* から:

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-one-shot-recognition"></a>"ワンショット" 認識を使用する

ユーザーが話す語句や文をリッスンするように音声認識エンジンを構成できます。 この例では、必要な入力の種類を音声認識エンジンに伝える *SpeechRecognitionTopicConstraint* を適用します。 このシナリオのアプリワークフローを次に示します。
1. アプリによって SpeechRecognizer が作成され、UI プロンプトが表示され、音声コマンドのリッスンが開始されます。
2. ユーザーは、語句または文を読み上げます。
3. ユーザーの音声認識が発生し、結果がアプリに返されます。 この時点で、アプリは、認識が発生したことを示す UI プロンプトを提供する必要があります。
4. 応答する信頼レベルと音声認識の結果の信頼レベルに応じて、アプリは結果を処理し、必要に応じて応答することができます。

このセクションでは、SpeechRecognizer を作成し、制約をコンパイルして、音声入力をリッスンする方法について説明します。

次のコードでは、トピック制約をコンパイルします。この場合、この例では web 検索用に最適化されています。

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

コンパイルが成功した場合は、音声認識を続行できます。

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

その後、結果がアプリに返されます。 結果に十分な確信があれば、コマンドを処理することができます。 このコード例では、少なくとも中程度の自信を持つ結果を処理します。

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

音声認識を使用する場合は常に、ユーザーがシステムのプライバシー設定でマイクをオフにしたことを示す例外を監視します。 これは、初期化または認識中に発生する可能性があります。

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

> [!NOTE]
> 音声認識を最適化するために使用できる定義済みの [SpeechRecognitionScenarios](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionScenario) がいくつかあります。

* ディクテーション用に最適化するには、ディクテーションのシナリオを使用します。<br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* Speech web 検索の場合は、次の web 固有のシナリオ制約を使用します。

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* フォームを入力するには、フォームの制約を使用します。 この場合は、フォームを入力するために最適化された独自の文法を適用することをお勧めします。

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* SRGS 形式で独自の文法を提供できます。

## <a name="use-continuous-recognition"></a>連続認識を使用する

連続ディクテーションのシナリオについては、「 [Windows 10 UWP speech コードサンプル](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)」を参照してください。

## <a name="handle-quality-degradation"></a>品質低下を処理する

環境の状況によっては、音声認識が妨げられることがあります。 たとえば、部屋の雑音が多すぎる場合や、ユーザーの声が大きすぎる場合があります。 音声認識 API は、可能な限り品質低下の原因となった状況に関する情報を提供します。 この情報は、WinRT イベントを使用してアプリにプッシュされます。 次の例は、このイベントをサブスクライブする方法を示しています。

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

このコードサンプルでは、条件情報をデバッグコンソールに書き込みます。 アプリは、UI、音声合成、および別の方法を使用してユーザーにフィードバックを提供することがあります。 または、品質の一時的な低下によって音声が中断されると、動作が異なる場合があります。

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

参照クラスを使用して DirectX アプリを作成しない場合は、音声認識エンジンをリリースまたは再作成する前に、イベントの登録を解除する必要があります。 HolographicSpeechPromptSample には、認識を停止し、イベントのサブスクライブを解除するルーチンがあります。

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a>音声合成を使用して音声入力のプロンプトを表示する

Holographic speech のサンプルでは、音声合成を使用してユーザーに可聴命令を提供します。 このセクションでは、合成された音声サンプルを作成し、HRTF audio Api を使用して再生する方法について説明します。

語句入力を要求するときに、独自の音声ガイダンスを提供することをお勧めします。 また、プロンプトを使用して、連続認識シナリオで音声コマンドを読み上げるタイミングを示すこともできます。 次の例は、音声シンセサイザーを使用してこれを行う方法を示しています。 事前に記録された音声クリップやビジュアル UI を使用することもできます。たとえば、プロンプトが動的でないシナリオでは、その他の説明を示すこともできます。

まず、SpeechSynthesizer オブジェクトを作成します。

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

合成するテキストを含む文字列も必要です。

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

音声は SynthesizeTextToStreamAsync を使用して非同期に合成されます。 ここでは、音声を合成する非同期タスクを開始します。

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

音声合成は、バイトストリームとして送信されます。 このバイトストリームを使用して、XAudio2 音声を初期化できます。 Holographic のコードサンプルでは、HRTF オーディオ効果として再生します。

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

音声認識と同様に、何らかの問題が発生した場合、音声合成は例外をスローします。

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a>関連項目
* [音声アプリの設計](/windows/uwp/design/input/speech-interactions)
* [SpeechRecognitionAndSynthesis サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)