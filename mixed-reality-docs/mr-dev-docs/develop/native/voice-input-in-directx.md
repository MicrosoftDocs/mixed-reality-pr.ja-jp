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
# <a name="voice-input-in-directx"></a><span data-ttu-id="9c8ba-104">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="9c8ba-104">Voice input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="9c8ba-105">この記事は、従来の WinRT ネイティブ Api に関連しています。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="9c8ba-106">新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](openxr-getting-started.md)** を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="9c8ba-107">この記事では、Windows Mixed Reality の DirectX アプリで [音声コマンド](../../design/voice-input.md) と小さな語句と文認識を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-107">This article explains how to implement [voice commands](../../design/voice-input.md) plus small-phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="9c8ba-108">この記事のコードスニペットは、 [C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用される c + c++ 17 準拠の c++/WinRT ではなく、c++/cx を使用します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-108">The code snippets in this article use C++/CX rather than C++17-compliant C++/WinRT, which is used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="9c8ba-109">概念は C++/WinRT プロジェクトに相当しますが、コードを変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-109">The concepts are equivalent for a C++/WinRT project, but you need to translate the code.</span></span>

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a><span data-ttu-id="9c8ba-110">SpeechRecognizer を使用して音声認識を継続する</span><span class="sxs-lookup"><span data-stu-id="9c8ba-110">Use SpeechRecognizer for continuous speech recognition</span></span>

<span data-ttu-id="9c8ba-111">このセクションでは、音声認識を使用してアプリで音声コマンドを有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-111">This section describes how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="9c8ba-112">このチュートリアルでは、 [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) サンプルのコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-112">This walk-through uses code from the [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) sample.</span></span> <span data-ttu-id="9c8ba-113">サンプルを実行している場合は、登録されているいずれかのカラーコマンドの名前を読み上げて、回転しているキューブの色を変更します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-113">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="9c8ba-114">最初に、新しい *Windows:: Media:: SpeechRecognition:: SpeechRecognizer* インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-114">First, create a new *Windows::Media::SpeechRecognition::SpeechRecognizer* instance.</span></span>

<span data-ttu-id="9c8ba-115">*HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState* から:</span><span class="sxs-lookup"><span data-stu-id="9c8ba-115">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="9c8ba-116">レコグナイザーがリッスンする音声コマンドのリストを作成します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-116">Create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="9c8ba-117">ここでは、ホログラムの色を変更するための一連のコマンドを作成します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-117">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="9c8ba-118">便宜上、後でコマンドに使用するデータも作成します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-118">For convenience, we also create the data that we'll use for the commands later.</span></span>

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

<span data-ttu-id="9c8ba-119">辞書に含まれていない可能性のある発音語を使用して、コマンドを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-119">You can use phonetic words that might not be in a dictionary to specify commands.</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="9c8ba-120">Speech レコグナイザーの制約の一覧にコマンドリストを読み込むには、 [SpeechRecognitionListConstraint](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint) オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-120">To load the commands list into the list of constraints for the speech recognizer, use a [SpeechRecognitionListConstraint](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint) object.</span></span>

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

<span data-ttu-id="9c8ba-121">音声認識エンジンの[SpeechContinuousRecognitionSession](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession)で[resultgenerated](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession)イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-121">Subscribe to the [ResultGenerated](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession) event on the speech recognizer's [SpeechContinuousRecognitionSession](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession).</span></span> <span data-ttu-id="9c8ba-122">このイベントは、いずれかのコマンドが認識されたときにアプリに通知します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-122">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="9c8ba-123">*Onresultgenerated* イベントハンドラーは、 [SpeechContinuousRecognitionResultGeneratedEventArgs](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionResultGeneratedEventArgs)インスタンス内のイベントデータを受信します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-123">Your *OnResultGenerated* event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionResultGeneratedEventArgs) instance.</span></span> <span data-ttu-id="9c8ba-124">確信度が定義したしきい値を超える場合、アプリはイベントが発生したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-124">If the confidence is greater than the threshold you defined, your app should note that the event happened.</span></span> <span data-ttu-id="9c8ba-125">後の更新ループで使用できるように、イベントデータを保存します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-125">Save the event data so that you can use it in a later update loop.</span></span>

<span data-ttu-id="9c8ba-126">*HolographicVoiceInputSampleMain* から:</span><span class="sxs-lookup"><span data-stu-id="9c8ba-126">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="9c8ba-127">このコード例では、ユーザーのコマンドに従って、回転したホログラムキューブの色を変更します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="9c8ba-128">*HolographicVoiceInputSampleMain:: Update* から:</span><span class="sxs-lookup"><span data-stu-id="9c8ba-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-one-shot-recognition"></a><span data-ttu-id="9c8ba-129">"ワンショット" 認識を使用する</span><span class="sxs-lookup"><span data-stu-id="9c8ba-129">Use "one-shot" recognition</span></span>

<span data-ttu-id="9c8ba-130">ユーザーが話す語句や文をリッスンするように音声認識エンジンを構成できます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-130">You can configure a speech recognizer to listen for phrases or sentences that the user speaks.</span></span> <span data-ttu-id="9c8ba-131">この例では、必要な入力の種類を音声認識エンジンに伝える *SpeechRecognitionTopicConstraint* を適用します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-131">In this case, we apply a *SpeechRecognitionTopicConstraint* that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="9c8ba-132">このシナリオのアプリワークフローを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-132">Here's an app workflow for this scenario:</span></span>
1. <span data-ttu-id="9c8ba-133">アプリによって SpeechRecognizer が作成され、UI プロンプトが表示され、音声コマンドのリッスンが開始されます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a spoken command.</span></span>
2. <span data-ttu-id="9c8ba-134">ユーザーは、語句または文を読み上げます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-134">The user speaks a phrase or sentence.</span></span>
3. <span data-ttu-id="9c8ba-135">ユーザーの音声認識が発生し、結果がアプリに返されます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-135">Recognition of the user's speech occurs, and a result is returned to the app.</span></span> <span data-ttu-id="9c8ba-136">この時点で、アプリは、認識が発生したことを示す UI プロンプトを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-136">At this point, your app should provide a UI prompt to indicate that recognition has occurred.</span></span>
4. <span data-ttu-id="9c8ba-137">応答する信頼レベルと音声認識の結果の信頼レベルに応じて、アプリは結果を処理し、必要に応じて応答することができます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-137">Depending on the confidence level that you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="9c8ba-138">このセクションでは、SpeechRecognizer を作成し、制約をコンパイルして、音声入力をリッスンする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="9c8ba-139">次のコードでは、トピック制約をコンパイルします。この場合、この例では web 検索用に最適化されています。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-139">The following code compiles the topic constraint, which in this case is optimized for web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="9c8ba-140">コンパイルが成功した場合は、音声認識を続行できます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-140">If compilation succeeds, we can continue with speech recognition.</span></span>

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

<span data-ttu-id="9c8ba-141">その後、結果がアプリに返されます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-141">The result is then returned to the app.</span></span> <span data-ttu-id="9c8ba-142">結果に十分な確信があれば、コマンドを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-142">If we're confident enough in the result, we can process the command.</span></span> <span data-ttu-id="9c8ba-143">このコード例では、少なくとも中程度の自信を持つ結果を処理します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-143">This code example processes results with at least medium confidence.</span></span>

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

<span data-ttu-id="9c8ba-144">音声認識を使用する場合は常に、ユーザーがシステムのプライバシー設定でマイクをオフにしたことを示す例外を監視します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-144">Whenever you use speech recognition, watch for exceptions that could indicate that the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="9c8ba-145">これは、初期化または認識中に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-145">This can happen during initialization or recognition.</span></span>

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
> <span data-ttu-id="9c8ba-146">音声認識を最適化するために使用できる定義済みの [SpeechRecognitionScenarios](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionScenario) がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-146">There are several predefined [SpeechRecognitionScenarios](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionScenario) that you can use to optimize speech recognition.</span></span>

* <span data-ttu-id="9c8ba-147">ディクテーション用に最適化するには、ディクテーションのシナリオを使用します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-147">To optimize for dictation, use the dictation scenario.</span></span><br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* <span data-ttu-id="9c8ba-148">Speech web 検索の場合は、次の web 固有のシナリオ制約を使用します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-148">For speech web searches, use the following web-specific scenario constraint.</span></span>

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* <span data-ttu-id="9c8ba-149">フォームを入力するには、フォームの制約を使用します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="9c8ba-150">この場合は、フォームを入力するために最適化された独自の文法を適用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-150">In this case, it's best to apply your own grammar that's optimized for filling out the form.</span></span>

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* <span data-ttu-id="9c8ba-151">SRGS 形式で独自の文法を提供できます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-151">You can provide your own grammar in the SRGS format.</span></span>

## <a name="use-continuous-recognition"></a><span data-ttu-id="9c8ba-152">連続認識を使用する</span><span class="sxs-lookup"><span data-stu-id="9c8ba-152">Use continuous recognition</span></span>

<span data-ttu-id="9c8ba-153">連続ディクテーションのシナリオについては、「 [Windows 10 UWP speech コードサンプル](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-153">For the continuous-dictation scenario, see the [Windows 10 UWP speech code sample](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span></span>

## <a name="handle-quality-degradation"></a><span data-ttu-id="9c8ba-154">品質低下を処理する</span><span class="sxs-lookup"><span data-stu-id="9c8ba-154">Handle quality degradation</span></span>

<span data-ttu-id="9c8ba-155">環境の状況によっては、音声認識が妨げられることがあります。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-155">Environmental conditions sometimes interfere with speech recognition.</span></span> <span data-ttu-id="9c8ba-156">たとえば、部屋の雑音が多すぎる場合や、ユーザーの声が大きすぎる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-156">For example, the room might be too noisy, or the user might speak too loudly.</span></span> <span data-ttu-id="9c8ba-157">音声認識 API は、可能な限り品質低下の原因となった状況に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-157">Whenever possible, the speech recognition API provides information about the conditions that caused the quality degradation.</span></span> <span data-ttu-id="9c8ba-158">この情報は、WinRT イベントを使用してアプリにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-158">This information is pushed to your app through a WinRT event.</span></span> <span data-ttu-id="9c8ba-159">次の例は、このイベントをサブスクライブする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-159">The following example shows  how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="9c8ba-160">このコードサンプルでは、条件情報をデバッグコンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-160">In our code sample, we write the conditions information to the debug console.</span></span> <span data-ttu-id="9c8ba-161">アプリは、UI、音声合成、および別の方法を使用してユーザーにフィードバックを提供することがあります。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-161">An app might want to provide feedback to the user through the UI, speech synthesis, and another method.</span></span> <span data-ttu-id="9c8ba-162">または、品質の一時的な低下によって音声が中断されると、動作が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-162">Or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="9c8ba-163">参照クラスを使用して DirectX アプリを作成しない場合は、音声認識エンジンをリリースまたは再作成する前に、イベントの登録を解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-163">If you're not using ref classes to create your DirectX app, you must unsubscribe from the event before you release or recreate your speech recognizer.</span></span> <span data-ttu-id="9c8ba-164">HolographicSpeechPromptSample には、認識を停止し、イベントのサブスクライブを解除するルーチンがあります。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-164">The HolographicSpeechPromptSample has a routine to stop recognition and unsubscribe from events.</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a><span data-ttu-id="9c8ba-165">音声合成を使用して音声入力のプロンプトを表示する</span><span class="sxs-lookup"><span data-stu-id="9c8ba-165">Use speech synthesis to provide audible prompts</span></span>

<span data-ttu-id="9c8ba-166">Holographic speech のサンプルでは、音声合成を使用してユーザーに可聴命令を提供します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-166">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="9c8ba-167">このセクションでは、合成された音声サンプルを作成し、HRTF audio Api を使用して再生する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-167">This section shows how to create a synthesized voice sample  and then play it back through the HRTF audio APIs.</span></span>

<span data-ttu-id="9c8ba-168">語句入力を要求するときに、独自の音声ガイダンスを提供することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-168">We recommend providing your own speech prompts when you request phrase input.</span></span> <span data-ttu-id="9c8ba-169">また、プロンプトを使用して、連続認識シナリオで音声コマンドを読み上げるタイミングを示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-169">Prompts can also help indicate when speech commands can be spoken for a continuous-recognition scenario.</span></span> <span data-ttu-id="9c8ba-170">次の例は、音声シンセサイザーを使用してこれを行う方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-170">The following example demonstrates how to use a speech synthesizer to do this.</span></span> <span data-ttu-id="9c8ba-171">事前に記録された音声クリップやビジュアル UI を使用することもできます。たとえば、プロンプトが動的でないシナリオでは、その他の説明を示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-171">You could also use a pre-recorded voice clip, a visual UI, or another indicator of what to say, for example in scenarios where the prompt isn't dynamic.</span></span>

<span data-ttu-id="9c8ba-172">まず、SpeechSynthesizer オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-172">First, create the SpeechSynthesizer object.</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="9c8ba-173">合成するテキストを含む文字列も必要です。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-173">You also need a string that includes the text to  synthesize.</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="9c8ba-174">音声は SynthesizeTextToStreamAsync を使用して非同期に合成されます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-174">Speech is synthesized asynchronously through SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="9c8ba-175">ここでは、音声を合成する非同期タスクを開始します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-175">Here, we start an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="9c8ba-176">音声合成は、バイトストリームとして送信されます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-176">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="9c8ba-177">このバイトストリームを使用して、XAudio2 音声を初期化できます。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-177">We can use that byte stream to initialize an XAudio2 voice.</span></span> <span data-ttu-id="9c8ba-178">Holographic のコードサンプルでは、HRTF オーディオ効果として再生します。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-178">For our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="9c8ba-179">音声認識と同様に、何らかの問題が発生した場合、音声合成は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="9c8ba-179">As with speech recognition, speech synthesis throws an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9c8ba-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c8ba-180">See also</span></span>
* [<span data-ttu-id="9c8ba-181">音声アプリの設計</span><span class="sxs-lookup"><span data-stu-id="9c8ba-181">Speech app design</span></span>](/windows/uwp/design/input/speech-interactions)
* [<span data-ttu-id="9c8ba-182">SpeechRecognitionAndSynthesis サンプル</span><span class="sxs-lookup"><span data-stu-id="9c8ba-182">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)