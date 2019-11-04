---
title: DirectX での音声入力
description: Windows Mixed Reality の DirectX アプリで音声コマンドと小さなフレーズと文の認識を実装する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: チュートリアル、音声コマンド、語句、認識、音声、directx、プラットフォーム、cortana、windows mixed reality
ms.openlocfilehash: be8c0e570a0e112e01b580ad571c06fe3482ff9f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437192"
---
# <a name="voice-input-in-directx"></a>DirectX での音声入力

このトピックでは、Windows Mixed Reality の DirectX アプリで[音声コマンド](voice-input.md)を実装する方法と、小さなフレーズと文の認識を実装する方法について説明します。

>[!NOTE]
>この記事のコードスニペットでは、現在、 C++ [ C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用されてC++いる C + c++ 17 準拠の/WinRT ではなく、/cx の使用方法を示しています。  これらの概念は、プロジェクトC++の場合と同じですが、コードを変換する必要があります。

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a>音声コマンドを継続的に認識するために SpeechRecognizer を使用する

このセクションでは、音声認識を使用してアプリで音声コマンドを有効にする方法について説明します。 このチュートリアルでは、 [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964)サンプルのコードを使用します。 サンプルを実行している場合は、登録されているいずれかのカラーコマンドの名前を読み上げて、回転しているキューブの色を変更します。

最初に、新しい**Windows:: Media:: SpeechRecognition:: SpeechRecognizer**インスタンスを作成します。

*HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*から:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

レコグナイザーがリッスンする音声コマンドのリストを作成する必要があります。 ここでは、ホログラムの色を変更するための一連のコマンドを作成します。 利便性を高めるために、後でコマンドに使用するデータも作成します。

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

コマンドは、辞書に含まれていない可能性のある発音の単語を使用して指定できます。

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

コマンドの一覧が、音声認識エンジンの制約の一覧に読み込まれます。 これを行うには、 [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx)オブジェクトを使用します。

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

音声認識エンジンの[SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)で[resultgenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx)イベントをサブスクライブします。 このイベントは、いずれかのコマンドが認識されたときにアプリに通知します。

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

**Onresultgenerated**イベントハンドラーは、 [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx)インスタンス内のイベントデータを受信します。 定義したしきい値より信頼度が高い場合、アプリはイベントが発生したことを確認する必要があります。 後続の更新ループで使用できるように、イベントデータを保存します。

*HolographicVoiceInputSampleMain*から:

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

アプリのシナリオに適用されるデータを使用します。 このコード例では、ユーザーのコマンドに従って、回転したホログラムキューブの色を変更します。

*HolographicVoiceInputSampleMain:: Update*から:

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a>音声語句と文をワンショットで認識するためにディクテーションを使用する

ユーザーが読み上げる語句や文をリッスンするように音声認識エンジンを構成できます。 この例では、必要な入力の種類を音声認識エンジンに伝える SpeechRecognitionTopicConstraint を適用します。 この種類のユースケースでは、アプリのワークフローは次のようになります。
1. アプリによって SpeechRecognizer が作成され、UI プロンプトが表示され、すぐに読み上げるコマンドのリッスンが開始されます。
2. ユーザーは、語句または文を読み上げます。
3. ユーザーの音声認識が実行され、結果がアプリに返されます。 この時点で、アプリは認識が発生したことを示す UI プロンプトを提供する必要があります。
4. 応答する信頼レベルと音声認識の結果の信頼レベルに応じて、アプリは結果を処理し、必要に応じて応答することができます。

このセクションでは、SpeechRecognizer を作成し、制約をコンパイルして、音声入力をリッスンする方法について説明します。

次のコードでは、トピック制約をコンパイルします。この場合、この例では Web 検索用に最適化されています。

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

音声認識を使用する場合は常に、ユーザーがシステムのプライバシー設定でマイクをオフにしたことを示す例外を監視する必要があります。 これは、初期化中、または認識中に発生する可能性があります。

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

**注:** 音声認識を最適化するために、いくつかの定義済み[SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx)が用意されています。
* ディクテーション用に最適化する場合は、ディクテーションのシナリオを使用します。

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* 音声を使用して Web 検索を実行する場合は、次のように Web 固有のシナリオ制約を使用できます。

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
* SRGS 形式を使用して独自の文法を提供できます。

## <a name="use-continuous-freeform-speech-dictation"></a>連続した自由形式の音声ディクテーションを使用する

連続したディクテーションのシナリオについては、「Windows 10 UWP speech のコードサンプル」を参照してください[。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-degradation-in-quality"></a>品質の低下を処理する

環境内の条件によっては、音声認識の動作が妨げられることがあります。 たとえば、部屋の雑音が多すぎる場合や、ユーザーが音量を大きくしすぎる場合などです。 音声認識 API は、品質の低下の原因となった条件について、可能な限り情報を提供します。

この情報は、WinRT イベントを使用してアプリにプッシュされます。 このイベントをサブスクライブする方法の例を次に示します。

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

このコードサンプルでは、条件情報をデバッグコンソールに書き込むことを選択します。 アプリでは、UI や音声合成などを使用してユーザーにフィードバックを提供することができます。または、品質の一時的な低下によって音声が中断された場合に、動作が異なる場合があります。

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

参照クラスを使用して DirectX アプリを作成していない場合は、音声認識エンジンを解放または再作成する前に、イベントの登録を解除する必要があります。 HolographicSpeechPromptSample には、認識を停止し、次のようなイベントのサブスクリプションを解除するルーチンがあります。

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a>音声合成を使用して音声入力のプロンプトを表示する

Holographic speech のサンプルでは、音声合成を使用してユーザーに可聴命令を提供します。 このトピックでは、合成された音声サンプルを作成し、HRTF audio Api を使用して再生するプロセスについて説明します。

語句入力を要求するときは、独自の音声入力プロンプトを指定する必要があります。 これは、音声コマンドをいつでも認識できるようにする場合にも役立ちます。 音声シンセサイザーを使用してこれを行う方法の例を次に示します。また、メッセージが動的でない場合などに、事前に記録された音声クリップ、ビジュアル UI、またはその他の意見を示すインジケーターを使用することもできます。

まず、SpeechSynthesizer オブジェクトを作成します。

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

また、合成するテキストを含む文字列が必要です。

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

音声合成は、バイトストリームとして送信されます。 このバイトストリームを使用して、XAudio2 音声を初期化できます。holographic のコードサンプルでは、HRTF オーディオ効果として再生します。

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

音声認識と同様に、何らかの問題が発生した場合は、音声合成によって例外がスローされます。

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
* [音声アプリの設計](https://msdn.microsoft.com/library/dn596121.aspx)
* [DirectX の立体音響](spatial-sound-in-directx.md)
* [SpeechRecognitionAndSynthesis サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
