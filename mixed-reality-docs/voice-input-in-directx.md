---
title: DirectX での音声入力
description: Windows Mixed Reality の DirectX アプリで音声コマンドと小さなフレーズと文の認識を実装する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: チュートリアル、音声コマンド、語句、認識、音声、directx、プラットフォーム、cortana、windows mixed reality
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548667"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="c78f6-104">DirectX での音声入力</span><span class="sxs-lookup"><span data-stu-id="c78f6-104">Voice input in DirectX</span></span>

<span data-ttu-id="c78f6-105">このトピックでは、Windows Mixed Reality の DirectX アプリで[音声コマンド](voice-input.md)を実装する方法と、小さなフレーズと文の認識を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="c78f6-106">この記事のコードスニペットでは、現在、 C++ [ C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用されてC++いる C + c++ 17 準拠の/WinRT ではなく、/cx の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c78f6-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="c78f6-107">これらの概念は、プロジェクトC++の場合と同じですが、コードを変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c78f6-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="c78f6-108">音声コマンドを継続的に認識するために SpeechRecognizer を使用する</span><span class="sxs-lookup"><span data-stu-id="c78f6-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="c78f6-109">このセクションでは、音声認識を使用してアプリで音声コマンドを有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="c78f6-110">このチュートリアルでは、 [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964)サンプルのコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-110">This walkthrough uses code from the [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="c78f6-111">サンプルを実行している場合は、登録されているいずれかのカラーコマンドの名前を読み上げて、回転しているキューブの色を変更します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="c78f6-112">最初に、新しい**Windows:: Media:: SpeechRecognition:: SpeechRecognizer**インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="c78f6-113">*HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*から:</span><span class="sxs-lookup"><span data-stu-id="c78f6-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="c78f6-114">レコグナイザーがリッスンする音声コマンドのリストを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c78f6-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="c78f6-115">ここでは、ホログラムの色を変更するための一連のコマンドを作成します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="c78f6-116">利便性を高めるために、後でコマンドに使用するデータも作成します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

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

<span data-ttu-id="c78f6-117">コマンドは、辞書に含まれていない可能性のある発音の単語を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="c78f6-118">コマンドの一覧が、音声認識エンジンの制約の一覧に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="c78f6-119">これを行うには、 [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx)オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="c78f6-120">音声認識エンジンの[SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)で[resultgenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx)イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="c78f6-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="c78f6-121">このイベントは、いずれかのコマンドが認識されたときにアプリに通知します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="c78f6-122">**Onresultgenerated**イベントハンドラーは、 [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx)インスタンス内のイベントデータを受信します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="c78f6-123">定義したしきい値より信頼度が高い場合、アプリはイベントが発生したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c78f6-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="c78f6-124">後続の更新ループで使用できるように、イベントデータを保存します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="c78f6-125">*HolographicVoiceInputSampleMain*から:</span><span class="sxs-lookup"><span data-stu-id="c78f6-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="c78f6-126">アプリのシナリオに適用されるデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="c78f6-127">このコード例では、ユーザーのコマンドに従って、回転したホログラムキューブの色を変更します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="c78f6-128">*HolographicVoiceInputSampleMain:: Update*から:</span><span class="sxs-lookup"><span data-stu-id="c78f6-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="c78f6-129">音声語句と文をワンショットで認識するためにディクテーションを使用する</span><span class="sxs-lookup"><span data-stu-id="c78f6-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="c78f6-130">ユーザーが読み上げる語句や文をリッスンするように音声認識エンジンを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="c78f6-131">この例では、必要な入力の種類を音声認識エンジンに伝える SpeechRecognitionTopicConstraint を適用します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="c78f6-132">この種類のユースケースでは、アプリのワークフローは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c78f6-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="c78f6-133">アプリによって SpeechRecognizer が作成され、UI プロンプトが表示され、すぐに読み上げるコマンドのリッスンが開始されます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="c78f6-134">ユーザーは、語句または文を読み上げます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="c78f6-135">ユーザーの音声認識が実行され、結果がアプリに返されます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="c78f6-136">この時点で、アプリは認識が発生したことを示す UI プロンプトを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c78f6-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="c78f6-137">応答する信頼レベルと音声認識の結果の信頼レベルに応じて、アプリは結果を処理し、必要に応じて応答することができます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="c78f6-138">このセクションでは、SpeechRecognizer を作成し、制約をコンパイルして、音声入力をリッスンする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="c78f6-139">次のコードでは、トピック制約をコンパイルします。この場合、この例では Web 検索用に最適化されています。</span><span class="sxs-lookup"><span data-stu-id="c78f6-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="c78f6-140">コンパイルが成功した場合は、音声認識を続行できます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="c78f6-141">その後、結果がアプリに返されます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-141">The result is then returned to the app.</span></span> <span data-ttu-id="c78f6-142">結果に十分な確信があれば、コマンドを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="c78f6-143">このコード例では、少なくとも中程度の自信を持つ結果を処理します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-143">This code example processes results with at least Medium confidence.</span></span>

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

<span data-ttu-id="c78f6-144">音声認識を使用する場合は常に、ユーザーがシステムのプライバシー設定でマイクをオフにしたことを示す例外を監視する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c78f6-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="c78f6-145">これは、初期化中、または認識中に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c78f6-145">This can happen during initialization, or during recognition.</span></span>

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

<span data-ttu-id="c78f6-146">**注:** 音声認識を最適化するために、いくつかの定義済み[SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx)が用意されています。</span><span class="sxs-lookup"><span data-stu-id="c78f6-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="c78f6-147">ディクテーション用に最適化する場合は、ディクテーションのシナリオを使用します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="c78f6-148">音声を使用して Web 検索を実行する場合は、次のように Web 固有のシナリオ制約を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="c78f6-149">フォームを入力するには、フォームの制約を使用します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="c78f6-150">この場合は、フォームを入力するために最適化された独自の文法を適用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c78f6-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="c78f6-151">SRGS 形式を使用して独自の文法を提供できます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="c78f6-152">連続した自由形式の音声ディクテーションを使用する</span><span class="sxs-lookup"><span data-stu-id="c78f6-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="c78f6-153">連続したディクテーションのシナリオについては、「Windows 10 UWP speech のコードサンプル」を参照してください[。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="c78f6-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="c78f6-154">品質の低下を処理する</span><span class="sxs-lookup"><span data-stu-id="c78f6-154">Handle degradation in quality</span></span>

<span data-ttu-id="c78f6-155">環境内の条件によっては、音声認識の動作が妨げられることがあります。</span><span class="sxs-lookup"><span data-stu-id="c78f6-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="c78f6-156">たとえば、部屋の雑音が多すぎる場合や、ユーザーが音量を大きくしすぎる場合などです。</span><span class="sxs-lookup"><span data-stu-id="c78f6-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="c78f6-157">音声認識 API は、品質の低下の原因となった条件について、可能な限り情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="c78f6-158">この情報は、WinRT イベントを使用してアプリにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="c78f6-159">このイベントをサブスクライブする方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="c78f6-160">このコードサンプルでは、条件情報をデバッグコンソールに書き込むことを選択します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="c78f6-161">アプリでは、UI や音声合成などを使用してユーザーにフィードバックを提供することができます。または、品質の一時的な低下によって音声が中断された場合に、動作が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c78f6-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="c78f6-162">参照クラスを使用して DirectX アプリを作成していない場合は、音声認識エンジンを解放または再作成する前に、イベントの登録を解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c78f6-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="c78f6-163">HolographicSpeechPromptSample には、認識を停止し、次のようなイベントのサブスクリプションを解除するルーチンがあります。</span><span class="sxs-lookup"><span data-stu-id="c78f6-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="c78f6-164">音声合成を使用して音声入力のプロンプトを表示する</span><span class="sxs-lookup"><span data-stu-id="c78f6-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="c78f6-165">Holographic speech のサンプルでは、音声合成を使用してユーザーに可聴命令を提供します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="c78f6-166">このトピックでは、合成された音声サンプルを作成し、HRTF audio Api を使用して再生するプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="c78f6-167">語句入力を要求するときは、独自の音声入力プロンプトを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c78f6-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="c78f6-168">これは、音声コマンドをいつでも認識できるようにする場合にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="c78f6-169">音声シンセサイザーを使用してこれを行う方法の例を次に示します。また、メッセージが動的でない場合などに、事前に記録された音声クリップ、ビジュアル UI、またはその他の意見を示すインジケーターを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="c78f6-170">まず、SpeechSynthesizer オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="c78f6-171">また、合成するテキストを含む文字列が必要です。</span><span class="sxs-lookup"><span data-stu-id="c78f6-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="c78f6-172">音声は SynthesizeTextToStreamAsync を使用して非同期に合成されます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="c78f6-173">ここでは、音声を合成する非同期タスクを開始します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="c78f6-174">音声合成は、バイトストリームとして送信されます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="c78f6-175">このバイトストリームを使用して、XAudio2 音声を初期化できます。holographic のコードサンプルでは、HRTF オーディオ効果として再生します。</span><span class="sxs-lookup"><span data-stu-id="c78f6-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="c78f6-176">音声認識と同様に、何らかの問題が発生した場合は、音声合成によって例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c78f6-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c78f6-177">関連項目</span><span class="sxs-lookup"><span data-stu-id="c78f6-177">See also</span></span>
* [<span data-ttu-id="c78f6-178">音声アプリの設計</span><span class="sxs-lookup"><span data-stu-id="c78f6-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="c78f6-179">DirectX の立体音響</span><span class="sxs-lookup"><span data-stu-id="c78f6-179">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="c78f6-180">SpeechRecognitionAndSynthesis サンプル</span><span class="sxs-lookup"><span data-stu-id="c78f6-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
