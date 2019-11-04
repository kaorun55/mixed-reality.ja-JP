---
title: Unity での音声入力
description: Unity では、Windows Mixed Reality アプリケーションに音声入力を追加する3つの方法が公開されています。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 音声入力、KeywordRecognizer、GrammarRecognizer、マイク、ディクテーション、音声
ms.openlocfilehash: d1cd2a2b954a195bc3f2688d915965f89aa30f98
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438201"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="e9627-104">Unity での音声入力</span><span class="sxs-lookup"><span data-stu-id="e9627-104">Voice input in Unity</span></span>

>[!NOTE]
><span data-ttu-id="e9627-105">以下の情報の代わりに、音声認識の精度を大幅に向上させ、音声からテキストへのデコードや、ダイアログ、目的に応じた高度な音声の機能に簡単にアクセスできるようにする、認識音声サービス SDK の Unity プラグインの使用を検討してください。相互作用、翻訳、テキスト合成合成、自然言語音声認識。</span><span class="sxs-lookup"><span data-stu-id="e9627-105">Instead of the below information, consider using the Unity plug-in for the Cognitive Speech Services SDK which has much better Speech Accuracy results and provides easy access to speech-to-text decode and advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis and natural language speech recognition.</span></span> <span data-ttu-id="e9627-106">サンプルとドキュメントは次の場所にあります。 https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity</span><span class="sxs-lookup"><span data-stu-id="e9627-106">Find the sample and documentaion here: https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity</span></span>   

<span data-ttu-id="e9627-107">Unity では、Unity アプリケーションに[音声入力](voice-input.md)を追加する3つの方法が公開されています。</span><span class="sxs-lookup"><span data-stu-id="e9627-107">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="e9627-108">KeywordRecognizer (2 種類の PhraseRecognizers のいずれか) では、アプリには、リッスンする文字列コマンドの配列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e9627-108">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="e9627-109">GrammarRecognizer (他の種類の PhraseRecognizer) では、リッスンする特定の文法を定義する SRGS ファイルをアプリに与えることができます。</span><span class="sxs-lookup"><span data-stu-id="e9627-109">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="e9627-110">DictationRecognizer を使用すると、アプリは任意の単語をリッスンし、ユーザーにノートやその他の音声の表示を提供できます。</span><span class="sxs-lookup"><span data-stu-id="e9627-110">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="e9627-111">ディクテーションまたはフレーズ認識だけを一度に処理できます。</span><span class="sxs-lookup"><span data-stu-id="e9627-111">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="e9627-112">つまり、GrammarRecognizer または KeywordRecognizer がアクティブである場合、DictationRecognizer をアクティブにすることはできず、その逆も可能です。</span><span class="sxs-lookup"><span data-stu-id="e9627-112">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="e9627-113">音声用の機能を有効にする</span><span class="sxs-lookup"><span data-stu-id="e9627-113">Enabling the capability for Voice</span></span>

<span data-ttu-id="e9627-114">音声入力を利用するには、**マイク**の機能がアプリに対して宣言されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9627-114">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="e9627-115">Unity エディターで、[Edit > Project Settings > Player] の順に移動して、windows media player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="e9627-115">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="e9627-116">[Windows ストア] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9627-116">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="e9627-117">[発行設定 > 機能] セクションで、**マイク**の機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="e9627-117">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="e9627-118">フレーズ認識</span><span class="sxs-lookup"><span data-stu-id="e9627-118">Phrase Recognition</span></span>

<span data-ttu-id="e9627-119">ユーザーによって読み上げられた特定の語句をアプリでリッスンできるようにするには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9627-119">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="e9627-120">KeywordRecognizer または GrammarRecognizer を使用してリッスンする語句を指定します</span><span class="sxs-lookup"><span data-stu-id="e9627-120">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="e9627-121">OnPhraseRecognized イベントを処理し、認識された語句に対応するアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="e9627-121">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="e9627-122">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="e9627-122">KeywordRecognizer</span></span>

<span data-ttu-id="e9627-123">**名前空間:** *Unityengine。 Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="e9627-123">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="e9627-124">**型:** *KeywordRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="e9627-124">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="e9627-125">一部のキーストロークを保存するには、いくつかの using ステートメントが必要です。</span><span class="sxs-lookup"><span data-stu-id="e9627-125">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="e9627-126">次に、クラスにいくつかのフィールドを追加して、レコグナイザーとキーワード > アクションディクショナリを格納します。</span><span class="sxs-lookup"><span data-stu-id="e9627-126">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="e9627-127">次に、キーワードを辞書に追加します (Start () メソッドの内部など)。</span><span class="sxs-lookup"><span data-stu-id="e9627-127">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="e9627-128">この例では、"activate" キーワードを追加しています。</span><span class="sxs-lookup"><span data-stu-id="e9627-128">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="e9627-129">キーワードレコグナイザーを作成し、認識する内容を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9627-129">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="e9627-130">次に、OnPhraseRecognized イベントに登録します。</span><span class="sxs-lookup"><span data-stu-id="e9627-130">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="e9627-131">ハンドラーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e9627-131">An example handler is:</span></span>

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

<span data-ttu-id="e9627-132">最後に、認識を開始します。</span><span class="sxs-lookup"><span data-stu-id="e9627-132">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="e9627-133">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="e9627-133">GrammarRecognizer</span></span>

<span data-ttu-id="e9627-134">**名前空間:** *Unityengine。 Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="e9627-134">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="e9627-135">**型**: *GrammarRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="e9627-135">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="e9627-136">GrammarRecognizer は、SRGS を使用して認識文法を指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="e9627-136">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="e9627-137">これは、アプリにいくつかのキーワードしか含まれていない場合、より複雑な語句を認識する場合、またはコマンドのセットを簡単にオン/オフにする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="e9627-137">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="e9627-138">詳細については、「 [SRGS XML を使用して](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx)ファイル形式情報を作成する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9627-138">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="e9627-139">SRGS 文法を取得し、それがプロジェクト内の[Streamingassets フォルダー](https://docs.unity3d.com/Manual/StreamingAssets.html)にある場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e9627-139">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="e9627-140">GrammarRecognizer を作成し、SRGS ファイルへのパスを渡します。</span><span class="sxs-lookup"><span data-stu-id="e9627-140">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="e9627-141">次に、OnPhraseRecognized イベントに登録します。</span><span class="sxs-lookup"><span data-stu-id="e9627-141">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="e9627-142">必要に応じて処理できる、SRGS 文法に指定されている情報を含むコールバックが取得されます。</span><span class="sxs-lookup"><span data-stu-id="e9627-142">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="e9627-143">重要な情報の大部分は、semanticMeanings 配列に記載されています。</span><span class="sxs-lookup"><span data-stu-id="e9627-143">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="e9627-144">最後に、認識を開始します。</span><span class="sxs-lookup"><span data-stu-id="e9627-144">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="e9627-145">ディクテーション</span><span class="sxs-lookup"><span data-stu-id="e9627-145">Dictation</span></span>

<span data-ttu-id="e9627-146">**名前空間:** *Unityengine。 Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="e9627-146">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="e9627-147">**型**: *DictationRecognizer*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="e9627-147">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="e9627-148">DictationRecognizer を使用して、ユーザーの音声をテキストに変換します。</span><span class="sxs-lookup"><span data-stu-id="e9627-148">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="e9627-149">DictationRecognizer は[ディクテーション](voice-input.md#dictation)機能を公開しており、仮説と語句の完了イベントの登録とリッスンをサポートしているので、ユーザーが話すときと後の両方でユーザーにフィードバックを提供できます。</span><span class="sxs-lookup"><span data-stu-id="e9627-149">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="e9627-150">Start () メソッドと Stop () メソッドは、それぞれディクテーション認識を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="e9627-150">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="e9627-151">レコグナイザーを使用したら、Dispose () メソッドを使用して破棄し、使用するリソースを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9627-151">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="e9627-152">これらのリソースは、それより前にリリースされていない場合、追加のパフォーマンスコストで、ガベージコレクション中に自動的に解放されます。</span><span class="sxs-lookup"><span data-stu-id="e9627-152">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="e9627-153">ディクテーションを開始するには、いくつかの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9627-153">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="e9627-154">新しい DictationRecognizer を作成する</span><span class="sxs-lookup"><span data-stu-id="e9627-154">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="e9627-155">ディクテーションイベントの処理</span><span class="sxs-lookup"><span data-stu-id="e9627-155">Handle Dictation events</span></span>
3. <span data-ttu-id="e9627-156">DictationRecognizer を開始する</span><span class="sxs-lookup"><span data-stu-id="e9627-156">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="e9627-157">ディクテーション用の機能を有効にする</span><span class="sxs-lookup"><span data-stu-id="e9627-157">Enabling the capability for dictation</span></span>

<span data-ttu-id="e9627-158">"インターネットクライアント" 機能は、前述の "マイク" 機能に加えて、ディクテーションを利用するためにアプリに対して宣言されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9627-158">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="e9627-159">Unity エディターで、[Edit > Project Settings > Player] ページに移動して、windows media player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="e9627-159">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="e9627-160">[Windows ストア] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9627-160">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="e9627-161">[発行の設定 > 機能] セクションで、 **Internetclient**の機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="e9627-161">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="e9627-162">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="e9627-162">DictationRecognizer</span></span>

<span data-ttu-id="e9627-163">次のような DictationRecognizer を作成します。</span><span class="sxs-lookup"><span data-stu-id="e9627-163">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="e9627-164">ディクテーションの動作を実装するためにサブスクライブおよび処理できるディクテーションイベントは4つあります。</span><span class="sxs-lookup"><span data-stu-id="e9627-164">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="e9627-165">DictationResult</span><span class="sxs-lookup"><span data-stu-id="e9627-165">DictationResult</span></span>
2. <span data-ttu-id="e9627-166">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="e9627-166">DictationComplete</span></span>
3. <span data-ttu-id="e9627-167">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="e9627-167">DictationHypothesis</span></span>
4. <span data-ttu-id="e9627-168">DictationError</span><span class="sxs-lookup"><span data-stu-id="e9627-168">DictationError</span></span>

<span data-ttu-id="e9627-169">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="e9627-169">**DictationResult**</span></span>

<span data-ttu-id="e9627-170">このイベントは、ユーザーが一時停止した後、通常は文の最後に発生します。</span><span class="sxs-lookup"><span data-stu-id="e9627-170">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="e9627-171">完全に認識された文字列がここに返されます。</span><span class="sxs-lookup"><span data-stu-id="e9627-171">The full recognized string is returned here.</span></span>

<span data-ttu-id="e9627-172">まず、DictationResult イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="e9627-172">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="e9627-173">次に、DictationResult コールバックを処理します。</span><span class="sxs-lookup"><span data-stu-id="e9627-173">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="e9627-174">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="e9627-174">**DictationHypothesis**</span></span>

<span data-ttu-id="e9627-175">このイベントは、ユーザーが話している間、継続的に発生します。</span><span class="sxs-lookup"><span data-stu-id="e9627-175">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="e9627-176">認識エンジンがリッスンすると、これまでに知られている内容のテキストが提供されます。</span><span class="sxs-lookup"><span data-stu-id="e9627-176">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="e9627-177">まず、DictationHypothesis イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="e9627-177">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="e9627-178">次に、DictationHypothesis コールバックを処理します。</span><span class="sxs-lookup"><span data-stu-id="e9627-178">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="e9627-179">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="e9627-179">**DictationComplete**</span></span>

<span data-ttu-id="e9627-180">このイベントは、レコグナイザー () が呼び出されているか、タイムアウトが発生したか、またはその他のエラーが発生した場合に、レコグナイザーが停止したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="e9627-180">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="e9627-181">まず、DictationComplete イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="e9627-181">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="e9627-182">次に、DictationComplete コールバックを処理します。</span><span class="sxs-lookup"><span data-stu-id="e9627-182">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="e9627-183">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="e9627-183">**DictationError**</span></span>

<span data-ttu-id="e9627-184">このイベントは、エラーが発生したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="e9627-184">This event is fired when an error occurs.</span></span>

<span data-ttu-id="e9627-185">まず、DictationError イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="e9627-185">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="e9627-186">次に、DictationError コールバックを処理します。</span><span class="sxs-lookup"><span data-stu-id="e9627-186">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="e9627-187">使用するディクテーションイベントをサブスクライブして処理したら、ディクテーションエンジンを起動してイベントの受信を開始します。</span><span class="sxs-lookup"><span data-stu-id="e9627-187">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="e9627-188">DictationRecognizer を維持する必要がなくなった場合は、イベントのサブスクリプションを解除し、DictationRecognizer を破棄する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9627-188">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="e9627-189">**テクニック**</span><span class="sxs-lookup"><span data-stu-id="e9627-189">**Tips**</span></span>
* <span data-ttu-id="e9627-190">Start () メソッドと Stop () メソッドは、それぞれディクテーション認識を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="e9627-190">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="e9627-191">レコグナイザーを使用したら、Dispose () メソッドを使用して破棄し、使用するリソースを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9627-191">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="e9627-192">これらのリソースは、それより前にリリースされていない場合、追加のパフォーマンスコストで、ガベージコレクション中に自動的に解放されます。</span><span class="sxs-lookup"><span data-stu-id="e9627-192">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="e9627-193">タイムアウトは、一定の時間が経過すると発生します。</span><span class="sxs-lookup"><span data-stu-id="e9627-193">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="e9627-194">これらのタイムアウトは、DictationComplete イベントで確認できます。</span><span class="sxs-lookup"><span data-stu-id="e9627-194">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="e9627-195">次の2つの点に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9627-195">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="e9627-196">認識エンジンが起動し、最初の5秒間オーディオが聞こえない場合は、タイムアウトします。</span><span class="sxs-lookup"><span data-stu-id="e9627-196">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="e9627-197">認識エンジンが結果を指定した後、20秒間無音の状態になると、タイムアウトします。</span><span class="sxs-lookup"><span data-stu-id="e9627-197">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="e9627-198">語句認識とディクテーションの両方を使用する</span><span class="sxs-lookup"><span data-stu-id="e9627-198">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="e9627-199">アプリでフレーズ認識とディクテーションの両方を使用する場合は、もう一方を開始する前に、1つを完全にシャットダウンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9627-199">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="e9627-200">複数の KeywordRecognizers を実行している場合は、次のようにして一度にシャットダウンできます。</span><span class="sxs-lookup"><span data-stu-id="e9627-200">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="e9627-201">すべてのレコグナイザーを前の状態に復元するには、DictationRecognizer が停止した後、次のように呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e9627-201">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="e9627-202">KeywordRecognizer を開始することもできます。これにより、PhraseRecognitionSystem も再起動されます。</span><span class="sxs-lookup"><span data-stu-id="e9627-202">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="e9627-203">マイクヘルパーの使用</span><span class="sxs-lookup"><span data-stu-id="e9627-203">Using the microphone helper</span></span>

<span data-ttu-id="e9627-204">GitHub の Mixed Reality Toolkit には、システムに使用可能なマイクがある場合に開発者にヒントを表示するマイクヘルパークラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e9627-204">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="e9627-205">ここでの用途の1つは、システム上にマイクがあるかどうかを確認してから、アプリケーションで音声操作のヒントを表示することです。</span><span class="sxs-lookup"><span data-stu-id="e9627-205">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="e9627-206">マイクヘルパースクリプトは、[[入力/スクリプト/ユーティリティ] フォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)にあります。</span><span class="sxs-lookup"><span data-stu-id="e9627-206">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="e9627-207">GitHub リポジトリには、ヘルパーの使用方法を示す[小さなサンプル](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs)も含まれています。</span><span class="sxs-lookup"><span data-stu-id="e9627-207">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="e9627-208">混合 Reality ツールキットでの音声入力</span><span class="sxs-lookup"><span data-stu-id="e9627-208">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="e9627-209">このシーンでは、音声入力の例を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e9627-209">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="e9627-210">HoloToolkit-Examples/Input/シーン/SpeechInputSource</span><span class="sxs-lookup"><span data-stu-id="e9627-210">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
