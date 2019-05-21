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
# <a name="voice-input-in-unity"></a>Unity での音声入力

Unity を追加する 3 つの方法を公開する[音声入力](voice-input.md)Unity アプリケーションにします。

(PhraseRecognizers の 2 つの種類のいずれか) KeywordRecognizer、リッスンするようにコマンドを文字列の配列が指定することができますが、アプリ。 GrammarRecognizer (その他の種類 PhraseRecognizer) では、リッスンするように特定の文法を定義する、SRGS ファイルが指定することができますが、アプリ。 DictationRecognizer では、アプリは任意の単語をリッスンし、またはその他の表示、音声を使用して、ユーザーを提供します。

>[!NOTE]
>ディクテーションまたはフレーズ認識だけを一度に処理できます。 GrammarRecognizer または KeywordRecognizer がアクティブな場合、DictationRecognizer しないアクティブにできることを意味し、その逆です。

## <a name="enabling-the-capability-for-voice"></a>音声の機能を有効にします。

**マイク**音声入力を活用するアプリの機能を宣言する必要があります。
1. Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」に移動して、player の設定に移動します。
2. "Windows Store" タブをクリックします。
3. 「発行の設定 > 機能」セクションでは、確認、**マイク**機能

## <a name="phrase-recognition"></a>フレーズ認識

特定のリッスンするようにアプリを有効にするには、アクションを実行し、ユーザーが音声フレーズをする必要があります。
1. KeywordRecognizer または GrammarRecognizer を使用してリッスンするには、どのフレーズを指定します。
2. OnPhraseRecognized イベントを処理し、認識される語句に対応するアクションを実行

### <a name="keywordrecognizer"></a>KeywordRecognizer

**名前空間:** *UnityEngine.Windows.Speech*<br>
**種類:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

させていただきます。 いくつかのステートメントを使用して、一部のキー操作を保存します。

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

認識エンジンとキーワードを格納するクラスにいくつかのフィールドがアクションのディクショナリを -> を追加してみましょう。

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

(例: Start() メソッド) の内部辞書にキーワードを追加します。 この例では「アクティブ」キーワードを追加します。

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

キーワード認識エンジンを作成しを認識することを確認します。

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

OnPhraseRecognized イベントに登録されました

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

ハンドラーの例を示します。

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

最後に、開始を認識します。

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**名前空間:** *UnityEngine.Windows.Speech*<br>
**型**:*GrammarRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*

SRGS を使用して、認識文法を指定している場合、GrammarRecognizer が使用されます。 複雑なフレーズを認識する場合、アプリがより多くのキーワードがある場合、またはオンとオフのコマンド セットを簡単に有効にする場合は便利にできます。 参照トピック[文法を使用して SRGS XML 作成](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx)ファイル形式の情報。

SRGS 文法とプロジェクトでは、 [StreamingAssets フォルダー](http://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

GrammarRecognizer を作成し、SRGS ファイルへのパスを渡します。

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

OnPhraseRecognized イベントに登録されました

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

適切に処理できる、SRGS 文法で指定された情報を格納しているコールバックが表示されます。 重要な情報のほとんどは、semanticMeanings 配列で提供されます。

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

最後に、開始を認識します。

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>ディクテーション

**名前空間:** *UnityEngine.Windows.Speech*<br>
**型**:*DictationRecognizer*、 *SpeechError*、 *SpeechSystemStatus*

ユーザーの音声をテキストに変換するのに、DictationRecognizer を使用します。 DictationRecognizer 公開[ディクテーション](voice-input.md#dictation)機能とサポートを登録して、仮説と語句をリッスンしているため、それらを話すときに、ユーザーにフィードバックを提供することができます、イベントを完了し、その後です。 Start() と Stop() メソッドはそれぞれを有効にして、ディクテーション認識を無効にします。 完了すると、認識エンジンで、これは破棄されなければなりません Dispose() メソッドを使用して、使用するリソースを解放します。 リリースこれらのリソースに自動的に追加のパフォーマンス コストでガベージ コレクション中に場合より前は解放されません。

ディクテーション モードを開始するために必要ないくつかの手順のみがあります。
1. 新しい DictationRecognizer を作成します。
2. 音声入力イベントの処理
3. 開始、DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>ディクテーションの機能を有効にします。

ディクテーションを活用するアプリの上記のように「マイク」機能のほかに、「インターネット クライアント」機能を宣言する必要があります。
1. Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」のページに移動して、player の設定に移動します。
2. "Windows Store" タブをクリックします。
3. 「発行の設定 > 機能」セクションでは、確認、 **InternetClient**機能

### <a name="dictationrecognizer"></a>DictationRecognizer

作成、DictationRecognizer ようになります。

```
dictationRecognizer = new DictationRecognizer();
```

サブスクライブしているディクテーションの動作を実装するために処理できる 4 つの音声入力イベントがあります。
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

このイベントは、ユーザーの後に発生が一時停止した通常文の最後にします。 完全な認識、ここでは文字列が返されます。

まず、DictationResult イベントにサブスクライブします。

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

DictationResult コールバックを処理します。

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

このイベントは、ユーザーが対話中に継続的に発生します。 認識エンジンがリッスンするよう、対象のテキストを提供します。 これまでに聞いたこと。

まず、DictationHypothesis イベントにサブスクライブします。

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

DictationHypothesis コールバックを処理します。

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

このイベントには、Stop()、タイムアウトが発生している場合、またはその他のエラーは、呼び出されるかどうかを認識エンジンが停止したらが発生します。

まず、DictationComplete イベントにサブスクライブします。

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

DictationComplete コールバックを処理します。

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

このイベントは、エラーが発生したときに発生します。

まず、DictationError イベントにサブスクライブします。

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

DictationError コールバックを処理します。

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

サブスクライブして、関心のあるディクテーション イベントを処理すると、イベントの受信を開始するディクテーション認識エンジンを起動します。

```
dictationRecognizer.Start();
```

周り DictationRecognizer を保持する必要がなくなった場合は、イベント サブスクリプションを解除し、DictationRecognizer を破棄する必要があります。

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**ヒント**
* Start() と Stop() メソッドはそれぞれを有効にして、ディクテーション認識を無効にします。
* 完了すると、認識エンジンで、使用するリソースを解放する Dispose() メソッドを使用してで破棄されたします。 リリースこれらのリソースに自動的に追加のパフォーマンス コストでガベージ コレクション中に場合より前は解放されません。
* タイムアウトは、一定期間の後に発生します。 これらのタイムアウト DictationComplete イベントで確認できます。 注意すべき 2 つのタイムアウトがあります。
   1. 認識エンジンが起動し、最初の 5 秒間のオーディオの声が場合、タイムアウトになります。
   2. 認識エンジンが指定の結果を 20 秒の無音が場合がタイムアウトになります。

## <a name="using-both-phrase-recognition-and-dictation"></a>フレーズ認識とディクテーションの両方を使用

フレーズ認識とディクテーションの両方をアプリで使用する場合は、完全に 1 つ前にシャット ダウン、もう一方を開始する必要があります。 複数の KeywordRecognizers 実行した場合で停止できますそれらすべて一度にで。

```
PhraseRecognitionSystem.Shutdown();
```

DictationRecognizer が停止した後は、以前の状態にすべての認識機能を復元するために呼び出すことができます。

```
PhraseRecognitionSystem.Restart();
```

また、KeywordRecognizer も PhraseRecognitionSystem を再起動するだけでも開始でした。

## <a name="using-the-microphone-helper"></a>マイク ヘルパーの使用

GitHub の混合実際にはツールキットには、マイクのヘルパー クラスに、システムで使用可能なマイクがある場合は、開発者にヒントが含まれています。 その用途の 1 つは、場所がマイク システムで、アプリケーションで、音声の対話のヒントを表示する前にする 1 つです。

マイクのヘルパー スクリプトが記載されて、[入力、スクリプト、およびユーティリティ フォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)します。 GitHub リポジトリにも含まれています、[小さなサンプル](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs)ヘルパーを使用する方法について説明します。

## <a name="voice-input-in-mixed-reality-toolkit"></a>Mixed Reality toolkit の音声入力
このシーンでは、音声入力の例が見つかります。

- [HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
