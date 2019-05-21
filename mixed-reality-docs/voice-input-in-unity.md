---
title: Unity での音声入力
description: Unity では、Windows Mixed Reality アプリに音声入力を追加する 3 つの方法を公開します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 音声入力、KeywordRecognizer、GrammarRecognizer、マイク、ディクテーション、音声
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604818"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="894e3-104">Unity での音声入力</span><span class="sxs-lookup"><span data-stu-id="894e3-104">Voice input in Unity</span></span>

<span data-ttu-id="894e3-105">Unity を追加する 3 つの方法を公開する[音声入力](voice-input.md)Unity アプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="894e3-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="894e3-106">(PhraseRecognizers の 2 つの種類のいずれか) KeywordRecognizer、リッスンするようにコマンドを文字列の配列が指定することができますが、アプリ。</span><span class="sxs-lookup"><span data-stu-id="894e3-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="894e3-107">GrammarRecognizer (その他の種類 PhraseRecognizer) では、リッスンするように特定の文法を定義する、SRGS ファイルが指定することができますが、アプリ。</span><span class="sxs-lookup"><span data-stu-id="894e3-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="894e3-108">DictationRecognizer では、アプリは任意の単語をリッスンし、またはその他の表示、音声を使用して、ユーザーを提供します。</span><span class="sxs-lookup"><span data-stu-id="894e3-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="894e3-109">ディクテーションまたはフレーズ認識だけを一度に処理できます。</span><span class="sxs-lookup"><span data-stu-id="894e3-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="894e3-110">GrammarRecognizer または KeywordRecognizer がアクティブな場合、DictationRecognizer しないアクティブにできることを意味し、その逆です。</span><span class="sxs-lookup"><span data-stu-id="894e3-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="894e3-111">音声の機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="894e3-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="894e3-112">**マイク**音声入力を活用するアプリの機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="894e3-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="894e3-113">Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」に移動して、player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="894e3-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="894e3-114">"Windows Store" タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="894e3-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="894e3-115">「発行の設定 > 機能」セクションでは、確認、**マイク**機能</span><span class="sxs-lookup"><span data-stu-id="894e3-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="894e3-116">フレーズ認識</span><span class="sxs-lookup"><span data-stu-id="894e3-116">Phrase Recognition</span></span>

<span data-ttu-id="894e3-117">特定のリッスンするようにアプリを有効にするには、アクションを実行し、ユーザーが音声フレーズをする必要があります。</span><span class="sxs-lookup"><span data-stu-id="894e3-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="894e3-118">KeywordRecognizer または GrammarRecognizer を使用してリッスンするには、どのフレーズを指定します。</span><span class="sxs-lookup"><span data-stu-id="894e3-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="894e3-119">OnPhraseRecognized イベントを処理し、認識される語句に対応するアクションを実行</span><span class="sxs-lookup"><span data-stu-id="894e3-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="894e3-120">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="894e3-120">KeywordRecognizer</span></span>

<span data-ttu-id="894e3-121">**名前空間:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="894e3-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="894e3-122">**種類:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="894e3-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="894e3-123">させていただきます。 いくつかのステートメントを使用して、一部のキー操作を保存します。</span><span class="sxs-lookup"><span data-stu-id="894e3-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="894e3-124">認識エンジンとキーワードを格納するクラスにいくつかのフィールドがアクションのディクショナリを -> を追加してみましょう。</span><span class="sxs-lookup"><span data-stu-id="894e3-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="894e3-125">(例: Start() メソッド) の内部辞書にキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="894e3-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="894e3-126">この例では「アクティブ」キーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="894e3-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="894e3-127">キーワード認識エンジンを作成しを認識することを確認します。</span><span class="sxs-lookup"><span data-stu-id="894e3-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="894e3-128">OnPhraseRecognized イベントに登録されました</span><span class="sxs-lookup"><span data-stu-id="894e3-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="894e3-129">ハンドラーの例を示します。</span><span class="sxs-lookup"><span data-stu-id="894e3-129">An example handler is:</span></span>

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

<span data-ttu-id="894e3-130">最後に、開始を認識します。</span><span class="sxs-lookup"><span data-stu-id="894e3-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="894e3-131">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="894e3-131">GrammarRecognizer</span></span>

<span data-ttu-id="894e3-132">**名前空間:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="894e3-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="894e3-133">**型**:*GrammarRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="894e3-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="894e3-134">SRGS を使用して、認識文法を指定している場合、GrammarRecognizer が使用されます。</span><span class="sxs-lookup"><span data-stu-id="894e3-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="894e3-135">複雑なフレーズを認識する場合、アプリがより多くのキーワードがある場合、またはオンとオフのコマンド セットを簡単に有効にする場合は便利にできます。</span><span class="sxs-lookup"><span data-stu-id="894e3-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="894e3-136">参照トピック[文法を使用して SRGS XML 作成](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx)ファイル形式の情報。</span><span class="sxs-lookup"><span data-stu-id="894e3-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="894e3-137">SRGS 文法とプロジェクトでは、 [StreamingAssets フォルダー](http://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="894e3-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="894e3-138">GrammarRecognizer を作成し、SRGS ファイルへのパスを渡します。</span><span class="sxs-lookup"><span data-stu-id="894e3-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="894e3-139">OnPhraseRecognized イベントに登録されました</span><span class="sxs-lookup"><span data-stu-id="894e3-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="894e3-140">適切に処理できる、SRGS 文法で指定された情報を格納しているコールバックが表示されます。</span><span class="sxs-lookup"><span data-stu-id="894e3-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="894e3-141">重要な情報のほとんどは、semanticMeanings 配列で提供されます。</span><span class="sxs-lookup"><span data-stu-id="894e3-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="894e3-142">最後に、開始を認識します。</span><span class="sxs-lookup"><span data-stu-id="894e3-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="894e3-143">ディクテーション</span><span class="sxs-lookup"><span data-stu-id="894e3-143">Dictation</span></span>

<span data-ttu-id="894e3-144">**名前空間:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="894e3-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="894e3-145">**型**:*DictationRecognizer*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="894e3-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="894e3-146">ユーザーの音声をテキストに変換するのに、DictationRecognizer を使用します。</span><span class="sxs-lookup"><span data-stu-id="894e3-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="894e3-147">DictationRecognizer 公開[ディクテーション](voice-input.md#dictation)機能とサポートを登録して、仮説と語句をリッスンしているため、それらを話すときに、ユーザーにフィードバックを提供することができます、イベントを完了し、その後です。</span><span class="sxs-lookup"><span data-stu-id="894e3-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="894e3-148">Start() と Stop() メソッドはそれぞれを有効にして、ディクテーション認識を無効にします。</span><span class="sxs-lookup"><span data-stu-id="894e3-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="894e3-149">完了すると、認識エンジンで、これは破棄されなければなりません Dispose() メソッドを使用して、使用するリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="894e3-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="894e3-150">リリースこれらのリソースに自動的に追加のパフォーマンス コストでガベージ コレクション中に場合より前は解放されません。</span><span class="sxs-lookup"><span data-stu-id="894e3-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="894e3-151">ディクテーション モードを開始するために必要ないくつかの手順のみがあります。</span><span class="sxs-lookup"><span data-stu-id="894e3-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="894e3-152">新しい DictationRecognizer を作成します。</span><span class="sxs-lookup"><span data-stu-id="894e3-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="894e3-153">音声入力イベントの処理</span><span class="sxs-lookup"><span data-stu-id="894e3-153">Handle Dictation events</span></span>
3. <span data-ttu-id="894e3-154">開始、DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="894e3-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="894e3-155">ディクテーションの機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="894e3-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="894e3-156">ディクテーションを活用するアプリの上記のように「マイク」機能のほかに、「インターネット クライアント」機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="894e3-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="894e3-157">Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」のページに移動して、player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="894e3-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="894e3-158">"Windows Store" タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="894e3-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="894e3-159">「発行の設定 > 機能」セクションでは、確認、 **InternetClient**機能</span><span class="sxs-lookup"><span data-stu-id="894e3-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="894e3-160">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="894e3-160">DictationRecognizer</span></span>

<span data-ttu-id="894e3-161">作成、DictationRecognizer ようになります。</span><span class="sxs-lookup"><span data-stu-id="894e3-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="894e3-162">サブスクライブしているディクテーションの動作を実装するために処理できる 4 つの音声入力イベントがあります。</span><span class="sxs-lookup"><span data-stu-id="894e3-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="894e3-163">DictationResult</span><span class="sxs-lookup"><span data-stu-id="894e3-163">DictationResult</span></span>
2. <span data-ttu-id="894e3-164">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="894e3-164">DictationComplete</span></span>
3. <span data-ttu-id="894e3-165">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="894e3-165">DictationHypothesis</span></span>
4. <span data-ttu-id="894e3-166">DictationError</span><span class="sxs-lookup"><span data-stu-id="894e3-166">DictationError</span></span>

<span data-ttu-id="894e3-167">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="894e3-167">**DictationResult**</span></span>

<span data-ttu-id="894e3-168">このイベントは、ユーザーの後に発生が一時停止した通常文の最後にします。</span><span class="sxs-lookup"><span data-stu-id="894e3-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="894e3-169">完全な認識、ここでは文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="894e3-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="894e3-170">まず、DictationResult イベントにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="894e3-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="894e3-171">DictationResult コールバックを処理します。</span><span class="sxs-lookup"><span data-stu-id="894e3-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="894e3-172">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="894e3-172">**DictationHypothesis**</span></span>

<span data-ttu-id="894e3-173">このイベントは、ユーザーが対話中に継続的に発生します。</span><span class="sxs-lookup"><span data-stu-id="894e3-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="894e3-174">認識エンジンがリッスンするよう、対象のテキストを提供します。 これまでに聞いたこと。</span><span class="sxs-lookup"><span data-stu-id="894e3-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="894e3-175">まず、DictationHypothesis イベントにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="894e3-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="894e3-176">DictationHypothesis コールバックを処理します。</span><span class="sxs-lookup"><span data-stu-id="894e3-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="894e3-177">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="894e3-177">**DictationComplete**</span></span>

<span data-ttu-id="894e3-178">このイベントには、Stop()、タイムアウトが発生している場合、またはその他のエラーは、呼び出されるかどうかを認識エンジンが停止したらが発生します。</span><span class="sxs-lookup"><span data-stu-id="894e3-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="894e3-179">まず、DictationComplete イベントにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="894e3-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="894e3-180">DictationComplete コールバックを処理します。</span><span class="sxs-lookup"><span data-stu-id="894e3-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="894e3-181">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="894e3-181">**DictationError**</span></span>

<span data-ttu-id="894e3-182">このイベントは、エラーが発生したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="894e3-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="894e3-183">まず、DictationError イベントにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="894e3-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="894e3-184">DictationError コールバックを処理します。</span><span class="sxs-lookup"><span data-stu-id="894e3-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="894e3-185">サブスクライブして、関心のあるディクテーション イベントを処理すると、イベントの受信を開始するディクテーション認識エンジンを起動します。</span><span class="sxs-lookup"><span data-stu-id="894e3-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="894e3-186">周り DictationRecognizer を保持する必要がなくなった場合は、イベント サブスクリプションを解除し、DictationRecognizer を破棄する必要があります。</span><span class="sxs-lookup"><span data-stu-id="894e3-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="894e3-187">**ヒント**</span><span class="sxs-lookup"><span data-stu-id="894e3-187">**Tips**</span></span>
* <span data-ttu-id="894e3-188">Start() と Stop() メソッドはそれぞれを有効にして、ディクテーション認識を無効にします。</span><span class="sxs-lookup"><span data-stu-id="894e3-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="894e3-189">完了すると、認識エンジンで、使用するリソースを解放する Dispose() メソッドを使用してで破棄されたします。</span><span class="sxs-lookup"><span data-stu-id="894e3-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="894e3-190">リリースこれらのリソースに自動的に追加のパフォーマンス コストでガベージ コレクション中に場合より前は解放されません。</span><span class="sxs-lookup"><span data-stu-id="894e3-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="894e3-191">タイムアウトは、一定期間の後に発生します。</span><span class="sxs-lookup"><span data-stu-id="894e3-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="894e3-192">これらのタイムアウト DictationComplete イベントで確認できます。</span><span class="sxs-lookup"><span data-stu-id="894e3-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="894e3-193">注意すべき 2 つのタイムアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="894e3-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="894e3-194">認識エンジンが起動し、最初の 5 秒間のオーディオの声が場合、タイムアウトになります。</span><span class="sxs-lookup"><span data-stu-id="894e3-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="894e3-195">認識エンジンが指定の結果を 20 秒の無音が場合がタイムアウトになります。</span><span class="sxs-lookup"><span data-stu-id="894e3-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="894e3-196">フレーズ認識とディクテーションの両方を使用</span><span class="sxs-lookup"><span data-stu-id="894e3-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="894e3-197">フレーズ認識とディクテーションの両方をアプリで使用する場合は、完全に 1 つ前にシャット ダウン、もう一方を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="894e3-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="894e3-198">複数の KeywordRecognizers 実行した場合で停止できますそれらすべて一度にで。</span><span class="sxs-lookup"><span data-stu-id="894e3-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="894e3-199">DictationRecognizer が停止した後は、以前の状態にすべての認識機能を復元するために呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="894e3-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="894e3-200">また、KeywordRecognizer も PhraseRecognitionSystem を再起動するだけでも開始でした。</span><span class="sxs-lookup"><span data-stu-id="894e3-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="894e3-201">マイク ヘルパーの使用</span><span class="sxs-lookup"><span data-stu-id="894e3-201">Using the microphone helper</span></span>

<span data-ttu-id="894e3-202">GitHub の混合実際にはツールキットには、マイクのヘルパー クラスに、システムで使用可能なマイクがある場合は、開発者にヒントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="894e3-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="894e3-203">その用途の 1 つは、場所がマイク システムで、アプリケーションで、音声の対話のヒントを表示する前にする 1 つです。</span><span class="sxs-lookup"><span data-stu-id="894e3-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="894e3-204">マイクのヘルパー スクリプトが記載されて、[入力、スクリプト、およびユーティリティ フォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)します。</span><span class="sxs-lookup"><span data-stu-id="894e3-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="894e3-205">GitHub リポジトリにも含まれています、[小さなサンプル](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs)ヘルパーを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="894e3-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="894e3-206">Mixed Reality toolkit の音声入力</span><span class="sxs-lookup"><span data-stu-id="894e3-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="894e3-207">このシーンでは、音声入力の例が見つかります。</span><span class="sxs-lookup"><span data-stu-id="894e3-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="894e3-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span><span class="sxs-lookup"><span data-stu-id="894e3-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
