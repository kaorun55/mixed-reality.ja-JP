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
# <a name="voice-input-in-directx"></a><span data-ttu-id="c12b9-104">DirectX での音声入力</span><span class="sxs-lookup"><span data-stu-id="c12b9-104">Voice input in DirectX</span></span>

<span data-ttu-id="c12b9-105">このトピックでは、実装する方法を説明します[音声コマンド](voice-input.md)、および Windows Mixed Reality の DirectX アプリで小規模のフレーズと文と認識します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="c12b9-106">この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="c12b9-107">概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c12b9-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="c12b9-108">音声コマンドの認識を継続的なれている SpeechRecognizer で使用します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="c12b9-109">このセクションでは、継続的な音声認識を使用して、アプリに音声コマンドを有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="c12b9-110">このチュートリアルからコードを使用して、 [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964)サンプル。</span><span class="sxs-lookup"><span data-stu-id="c12b9-110">This walkthrough uses code from the [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="c12b9-111">サンプルを実行しているときに、回転するキューブの色を変更する登録済みの色のコマンドのいずれかの名前を読み上げます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="c12b9-112">最初に、作成、新しい**Windows::Media::SpeechRecognition::SpeechRecognizer**インスタンス。</span><span class="sxs-lookup"><span data-stu-id="c12b9-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="c12b9-113">*HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="c12b9-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="c12b9-114">リッスンするように、認識エンジンの音声コマンドの一覧を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c12b9-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="c12b9-115">ここでは、一連のホログラムの色を変更するコマンドを構築します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="c12b9-116">利便性を考えて、後で、コマンドを使用するデータも作成します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

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

<span data-ttu-id="c12b9-117">コマンドは、ディクショナリにできない可能性がある発音の単語を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="c12b9-118">コマンドの一覧は、音声認識エンジンの制約の一覧に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="c12b9-119">これを使用する[SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c12b9-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="c12b9-120">購読、 [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx)音声認識エンジンの上のイベント[SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="c12b9-121">このイベントでは、コマンドのいずれかが認識されているときに、アプリに通知します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="c12b9-122">**OnResultGenerated**イベント ハンドラーでイベント データを受信する、 [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="c12b9-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="c12b9-123">信頼度が定義したしきい値よりも大きい場合は、アプリは、イベントが発生したことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c12b9-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="c12b9-124">イベント データを保存できるように今後の更新プログラムのループで使用します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="c12b9-125">*HolographicVoiceInputSampleMain.cpp*:</span><span class="sxs-lookup"><span data-stu-id="c12b9-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="c12b9-126">作成ただし、アプリのシナリオに適用可能なデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="c12b9-127">このコード例では、ユーザーがコマンドに従ってスピン ホログラム キューブの色を変更します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="c12b9-128">*HolographicVoiceInputSampleMain::Update*:</span><span class="sxs-lookup"><span data-stu-id="c12b9-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="c12b9-129">ディクテーションを使用して、音声の語句や文の 1 回限りの認識</span><span class="sxs-lookup"><span data-stu-id="c12b9-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="c12b9-130">語句、またはユーザーが読み上げる文章をリッスンする音声認識エンジンを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="c12b9-131">この場合、期待する入力の種類、音声認識エンジンに指示する SpeechRecognitionTopicConstraint を適用します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="c12b9-132">アプリのワークフローは、この種類の使用例のとおり、です。</span><span class="sxs-lookup"><span data-stu-id="c12b9-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="c12b9-133">アプリを作成、れている SpeechRecognizer UI 画面の指示を提供し、すぐに読み上げられるコマンドのリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="c12b9-134">ユーザーは、語句、または文章を話します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="c12b9-135">ユーザーの音声の認識を実行すると、およびアプリに結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="c12b9-136">この時点では、アプリでは、認識が発生したことを示す UI プロンプトを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c12b9-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="c12b9-137">応答する信頼レベルと音声認識の結果の信頼レベルでは、によってアプリは、結果を処理し、適切な対応できます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="c12b9-138">このセクションには、れている SpeechRecognizer を作成し、制約をコンパイルして、音声入力をリッスンする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="c12b9-139">次のコードでは、ここで Web の検索に最適化されているトピックの「制約をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c12b9-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="c12b9-140">コンパイルが成功すると、音声認識で進むことができます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="c12b9-141">結果は、アプリに返されます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-141">The result is then returned to the app.</span></span> <span data-ttu-id="c12b9-142">結果に十分な確信しています場合のコマンドは、処理できます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="c12b9-143">このコード例では、少なくとも中程度の信頼度で結果を処理します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-143">This code example processes results with at least Medium confidence.</span></span>

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

<span data-ttu-id="c12b9-144">音声認識を使用するたびには、ユーザーがシステムのプライバシーの設定でマイクをオフになっていることを示す例外を監視します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="c12b9-145">これは、初期化中に、または認識中に発生することができます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-145">This can happen during initialization, or during recognition.</span></span>

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

<span data-ttu-id="c12b9-146">**注:** 定義済みのいくつかを使用する必要がある[SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx)音声認識を最適化するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="c12b9-147">ディクテーションを最適化する場合は、ディクテーション シナリオを使用します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="c12b9-148">音声認識を使用して、Web 検索を実行する、次のように Web に固有のシナリオの制約を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="c12b9-149">フォームの制約を使用すると、フォームに入力します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="c12b9-150">この場合は、フォームの入力用に最適化された独自の文法を適用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c12b9-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="c12b9-151">SRGS 形式を使用して、独自の文法を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="c12b9-152">Continuous、自由形式の音声認識を使用して、</span><span class="sxs-lookup"><span data-stu-id="c12b9-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="c12b9-153">継続的なディクテーション シナリオでは、Windows 10 UWP 音声認識のコード サンプルを参照してください。[ここです。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="c12b9-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="c12b9-154">品質の低下を処理します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-154">Handle degradation in quality</span></span>

<span data-ttu-id="c12b9-155">環境内の条件では、作業から音声認識を妨げることがあります。</span><span class="sxs-lookup"><span data-stu-id="c12b9-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="c12b9-156">たとえば、部屋のノイズが多すぎる可能性があります。 またはユーザーが高すぎるボリュームで話す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c12b9-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="c12b9-157">音声認識 API は、可能であれば、品質が低下した原因とする状態に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="c12b9-158">この情報は、WinRT イベントを使用してアプリにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="c12b9-159">このイベントをサブスクライブする方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="c12b9-160">このコード サンプルの条件の情報をデバッグ コンソールに書き込むを選択します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="c12b9-161">アプリは、UI、音声合成、およびを使用してユーザーにフィードバックを提供するまたは品質の一時的な低下によって音声を中断するときの動作が異なる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c12b9-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="c12b9-162">DirectX アプリを作成する ref クラスを使用していない場合は、解放や、音声認識エンジンを再作成する前に、イベントから解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c12b9-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="c12b9-163">HolographicSpeechPromptSample の認識を停止し、イベント サブスクリプションを解除するルーチンが次のようにします。</span><span class="sxs-lookup"><span data-stu-id="c12b9-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="c12b9-164">音声合成を使用して、音が聞こえる音声要求を提供するには</span><span class="sxs-lookup"><span data-stu-id="c12b9-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="c12b9-165">Holographic の音声認識のサンプルでは、音声合成を使用して、音の指示をユーザーに提供します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="c12b9-166">このトピックで、合成音声サンプルを作成して、HRTF オーディオ Api を使用して再生のプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="c12b9-167">独自の音声認識では、語句の入力を要求するときにメッセージが表示されますを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c12b9-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="c12b9-168">これも役に立ちますを示すための継続的な認識シナリオの音声コマンドをナレーションことができます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="c12b9-169">音声シンセサイザー; で操作する方法の例を示します録音済み音声メモやビジュアルの UI では、何を言おう、たとえば、プロンプトが動的ではないシナリオでは、その他のインジケーターも使用できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c12b9-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="c12b9-170">まず、SpeechSynthesizer オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="c12b9-171">合成するテキストの文字列も必要です。</span><span class="sxs-lookup"><span data-stu-id="c12b9-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="c12b9-172">音声は、非同期的に SynthesizeTextToStreamAsync を使用して合成します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="c12b9-173">ここでは、私たちは、音声合成する非同期タスクを開始します。</span><span class="sxs-lookup"><span data-stu-id="c12b9-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="c12b9-174">音声合成は、バイト ストリームとして送信されます。</span><span class="sxs-lookup"><span data-stu-id="c12b9-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="c12b9-175">そのバイト ストリームを使用して、XAudio2 音声を初期化できます。holographic のコード サンプルでは、私たちとして再生しない HRTF オーディオ効果。</span><span class="sxs-lookup"><span data-stu-id="c12b9-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="c12b9-176">として音声認識と音声合成例外がスローされます、問題が発生した場合。</span><span class="sxs-lookup"><span data-stu-id="c12b9-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c12b9-177">関連項目</span><span class="sxs-lookup"><span data-stu-id="c12b9-177">See also</span></span>
* [<span data-ttu-id="c12b9-178">音声認識型アプリの設計</span><span class="sxs-lookup"><span data-stu-id="c12b9-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="c12b9-179">DirectX での空間のサウンド</span><span class="sxs-lookup"><span data-stu-id="c12b9-179">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="c12b9-180">SpeechRecognitionAndSynthesis サンプル</span><span class="sxs-lookup"><span data-stu-id="c12b9-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
