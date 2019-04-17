---
title: DirectX での音声入力
description: Windows Mixed Reality の DirectX アプリでの音声コマンドやフレーズと文の小規模の認識を実装する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: チュートリアル、音声コマンド、フレーズ、認識、音声認識、directx、プラットフォーム、cortana、windows の複合現実
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605101"
---
# <a name="voice-input-in-directx"></a>DirectX での音声入力

このトピックでは、実装する方法を説明します[音声コマンド](voice-input.md)、および Windows Mixed Reality の DirectX アプリで小規模のフレーズと文と認識します。

>[!NOTE]
>この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。  概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a>音声コマンドの認識を継続的なれている SpeechRecognizer で使用します。

このセクションでは、継続的な音声認識を使用して、アプリに音声コマンドを有効にする方法について説明します。 このチュートリアルからコードを使用して、 [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964)サンプル。 サンプルを実行しているときに、回転するキューブの色を変更する登録済みの色のコマンドのいずれかの名前を読み上げます。

最初に、作成、新しい**Windows::Media::SpeechRecognition::SpeechRecognizer**インスタンス。

*HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

リッスンするように、認識エンジンの音声コマンドの一覧を作成する必要があります。 ここでは、一連のホログラムの色を変更するコマンドを構築します。 利便性を考えて、後で、コマンドを使用するデータも作成します。

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

コマンドは、ディクショナリにできない可能性がある発音の単語を使用して指定できます。

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

コマンドの一覧は、音声認識エンジンの制約の一覧に読み込まれます。 これを使用する[SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx)オブジェクト。

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

購読、 [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx)音声認識エンジンの上のイベント[SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)します。 このイベントでは、コマンドのいずれかが認識されているときに、アプリに通知します。

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

**OnResultGenerated**イベント ハンドラーでイベント データを受信する、 [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx)インスタンス。 信頼度が定義したしきい値よりも大きい場合は、アプリは、イベントが発生したことに注意してください。 イベント データを保存できるように今後の更新プログラムのループで使用します。

*HolographicVoiceInputSampleMain.cpp*:

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

作成ただし、アプリのシナリオに適用可能なデータを使用します。 このコード例では、ユーザーがコマンドに従ってスピン ホログラム キューブの色を変更します。

*HolographicVoiceInputSampleMain::Update*:

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a>ディクテーションを使用して、音声の語句や文の 1 回限りの認識

語句、またはユーザーが読み上げる文章をリッスンする音声認識エンジンを構成することができます。 この場合、期待する入力の種類、音声認識エンジンに指示する SpeechRecognitionTopicConstraint を適用します。 アプリのワークフローは、この種類の使用例のとおり、です。
1. アプリを作成、れている SpeechRecognizer UI 画面の指示を提供し、すぐに読み上げられるコマンドのリッスンを開始します。
2. ユーザーは、語句、または文章を話します。
3. ユーザーの音声の認識を実行すると、およびアプリに結果が返されます。 この時点では、アプリでは、認識が発生したことを示す UI プロンプトを提供する必要があります。
4. 応答する信頼レベルと音声認識の結果の信頼レベルでは、によってアプリは、結果を処理し、適切な対応できます。

このセクションには、れている SpeechRecognizer を作成し、制約をコンパイルして、音声入力をリッスンする方法について説明します。

次のコードでは、ここで Web の検索に最適化されているトピックの「制約をコンパイルします。

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

コンパイルが成功すると、音声認識で進むことができます。

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

結果は、アプリに返されます。 結果に十分な確信しています場合のコマンドは、処理できます。 このコード例では、少なくとも中程度の信頼度で結果を処理します。

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

音声認識を使用するたびには、ユーザーがシステムのプライバシーの設定でマイクをオフになっていることを示す例外を監視します。 これは、初期化中に、または認識中に発生することができます。

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

**注:** 定義済みのいくつかを使用する必要がある[SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx)音声認識を最適化するために使用できます。
* ディクテーションを最適化する場合は、ディクテーション シナリオを使用します。

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* 音声認識を使用して、Web 検索を実行する、次のように Web に固有のシナリオの制約を使用できます。

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* フォームの制約を使用すると、フォームに入力します。 この場合は、フォームの入力用に最適化された独自の文法を適用することをお勧めします。

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* SRGS 形式を使用して、独自の文法を行うことができます。

## <a name="use-continuous-freeform-speech-dictation"></a>Continuous、自由形式の音声認識を使用して、

継続的なディクテーション シナリオでは、Windows 10 UWP 音声認識のコード サンプルを参照してください。[ここです。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-degradation-in-quality"></a>品質の低下を処理します。

環境内の条件では、作業から音声認識を妨げることがあります。 たとえば、部屋のノイズが多すぎる可能性があります。 またはユーザーが高すぎるボリュームで話す可能性があります。 音声認識 API は、可能であれば、品質が低下した原因とする状態に関する情報を提供します。

この情報は、WinRT イベントを使用してアプリにプッシュされます。 このイベントをサブスクライブする方法の例を次に示します。

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

このコード サンプルの条件の情報をデバッグ コンソールに書き込むを選択します。 アプリは、UI、音声合成、およびを使用してユーザーにフィードバックを提供するまたは品質の一時的な低下によって音声を中断するときの動作が異なる必要があります。

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

DirectX アプリを作成する ref クラスを使用していない場合は、解放や、音声認識エンジンを再作成する前に、イベントから解除する必要があります。 HolographicSpeechPromptSample の認識を停止し、イベント サブスクリプションを解除するルーチンが次のようにします。

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a>音声合成を使用して、音が聞こえる音声要求を提供するには

Holographic の音声認識のサンプルでは、音声合成を使用して、音の指示をユーザーに提供します。 このトピックで、合成音声サンプルを作成して、HRTF オーディオ Api を使用して再生のプロセスについて説明します。

独自の音声認識では、語句の入力を要求するときにメッセージが表示されますを指定する必要があります。 これも役に立ちますを示すための継続的な認識シナリオの音声コマンドをナレーションことができます。 音声シンセサイザー; で操作する方法の例を示します録音済み音声メモやビジュアルの UI では、何を言おう、たとえば、プロンプトが動的ではないシナリオでは、その他のインジケーターも使用できることに注意してください。

まず、SpeechSynthesizer オブジェクトを作成します。

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

合成するテキストの文字列も必要です。

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

音声は、非同期的に SynthesizeTextToStreamAsync を使用して合成します。 ここでは、私たちは、音声合成する非同期タスクを開始します。

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

音声合成は、バイト ストリームとして送信されます。 そのバイト ストリームを使用して、XAudio2 音声を初期化できます。holographic のコード サンプルでは、私たちとして再生しない HRTF オーディオ効果。

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

として音声認識と音声合成例外がスローされます、問題が発生した場合。

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
* [音声認識型アプリの設計](https://msdn.microsoft.com/library/dn596121.aspx)
* [DirectX での空間のサウンド](spatial-sound-in-directx.md)
* [SpeechRecognitionAndSynthesis サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
