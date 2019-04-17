---
title: MR 入力 212 - 音声
description: 音声の概念の詳細については、Unity、Visual Studio および HoloLens を使用してこのコーディング チュートリアルに従ってください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit unity、academy、チュートリアルでは、音声
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598924"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br>

# <a name="mr-input-212-voice"></a>MR 入力 212:音声

[音声入力](voice-input.md)により、当社ホログラムと対話することもできます。 音声コマンドは、非常に自然で簡単な方法で機能します。 されるので、音声コマンドを設計します。

* 自然です
* 覚えやすい
* 適切なコンテキスト
* 同じコンテキスト内でその他のオプションを十分に区別

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

[MR 基本 101](holograms-101.md)、2 つの単純な音声コマンドの作成に、KeywordRecognizer を使いました。 MR 入力 212 でをについて詳しく知るし、学習する方法。

* HoloLens の音声認識エンジン用に最適化された音声コマンドをデザインします。
* コマンドの使用可能なは、どのような音声に注意してください、ユーザーを作成します。
* ユーザーの音声コマンドいただいてを確認します。
* ユーザーを理解という、ディクテーション認識エンジンを使用します。
* SRGS、または音声認識文法仕様ファイルに基づいてコマンドをリッスンするには、文法の認識エンジンを使用します。

このコースで思いますモデル エクスプ ローラーに組み込まれています[MR 入力 210](holograms-210.md)と[MR 入力 211](holograms-211.md)します。

>[!IMPORTANT]
>以前のバージョンの Unity と Mixed Reality Toolkit を使用して、以下の各章に埋め込まれたビデオが記録されています。 詳細な手順については、正確かつ最新ですが、スクリプトとは、無効な対応するビデオの中でビジュアルを表示があります。 ビデオでは、後生のために含まれる保持され、概念説明のため、引き続き適用されます。


## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 入力 212:音声</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始前の作業

### <a name="prerequisites"></a>前提条件

* 正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。
* 基本的なC#プログラミング機能。
* 完了する必要があります[MR 基本 101](holograms-101.md)します。
* 完了する必要があります[MR 入力 210](holograms-210.md)します。
* 完了する必要があります[MR 入力 211](holograms-211.md)します。
* HoloLens デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。

### <a name="project-files"></a>プロジェクト ファイル

* ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip)プロジェクトに必要です。 Unity 2017.2 またはそれ以降が必要です。
* 解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。

>[!NOTE]
>をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)します。

### <a name="errata-and-notes"></a>正誤表と注意事項

* 「マイ コードのみを有効にする」無効にする必要があります (*unchecked*) -> ツールの Visual Studio でのオプションには、デバッグ、コードにブレークポイントをヒットするには-> です。

## <a name="unity-setup"></a>Unity のセットアップ

### <a name="instructions"></a>手順

1. Unity を起動します。
2. **[開く]** を選択します。
3. 移動し、 **HolographicAcademy ホログラム 212 音声**フォルダー以前されていないアーカイブします。
4. 検索し、選択、**開始**/**モデル エクスプ ローラー**フォルダー。
5. をクリックして、**フォルダーの選択**ボタンをクリックします。
6. **プロジェクト**パネルで、展開、**シーン**フォルダー。
7. ダブルクリック**ModelExplorer**シーン Unity で読み込めません。

### <a name="building"></a>ビルド

1. Unity では、次のように選択します。**ファイル > Build Settings**します。
2. 場合**シーン/ModelExplorer**に記載されていない**Scenes In Build**、 をクリックして**開くシーンを追加**シーンを追加します。
3. 具体的には、HoloLens の開発中、設定**ターゲット デバイス**に**HoloLens**します。 それ以外の場合、残して**任意のデバイス**します。
4. 確認**ビルド タイプ**に設定されている**D3D**と**SDK**に設定されている**インストールされている最新**(16299 またはそれ以降の SDK がある必要があります)。
5. **[Build]** をクリックします。
6. 作成、**新しいフォルダー** "App"という名前です。
7. 1 回のクリック、**アプリ**フォルダー。
8. キーを押して**フォルダーの選択**Unity は Visual Studio のプロジェクトのビルドを開始します。

Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。

1. 開く、**アプリ**フォルダー。
2. 開く、 **ModelExplorer Visual Studio ソリューション**します。

HoloLens へのデプロイ: 場合

1. デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x86**します。
2. ローカル コンピューター] ボタンの横の矢印のドロップダウンをクリックし、[**リモート マシン**します。
3. 入力**HoloLens デバイスの IP アドレス**認証モードを設定および**ユニバーサル (暗号化されていないプロトコル)** します。 クリックして**選択**します。 デバイスの IP アドレスがわからない場合に参照**設定 > ネットワークとインターネット > 詳細オプション**します。
4. 上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。 最初に、デバイスに展開するには、する必要があります[Visual Studio をペアリング](using-visual-studio.md#pairing-your-device-hololens)します。
5. アプリが展開されると、消去、 **Fitbox**で、**ジェスチャ を選択**します。

場合は、イマーシブ ヘッドセットへのデプロイ。

1. デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x64**します。
2. 必ず、配置ターゲットに設定されて**ローカル マシン**します。
3. 上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。
4. アプリが展開されると、消去、 **Fitbox**アニメーション コント ローラーで、トリガーを取得することによって。

>[!NOTE]
>Visual Studio でエラー パネルの赤いエラーの一部が分かります。 それらを無視しても安全になります。 ビルドの進行状況を実際に表示する出力パネルへの切り替え。 エラー出力 パネルにでは修正プログラム (ほとんどの多くの場合、スクリプトで間違いに起因) を作成することが必要です。

## <a name="chapter-1---awareness"></a>第 1 章 - 認識

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>目標

* について説明します、**注意事項**の音声コマンド デザインします。
* 使用**KeywordRecognizer**視線入力ベースの音声コマンドを追加します。
* ユーザーがカーソルを使用して音声コマンドを認識させる**フィードバック**します。

### <a name="voice-command-design"></a>音声コマンド デザイン

この章では音声コマンドを設計する方法について説明します。 音声コマンドを作成する: 場合

#### <a name="do"></a>DO

* 簡潔なコマンドを作成します。 使用しない *「現在選択されているビデオを再生」*、そのコマンドが簡潔でないし、ユーザーが簡単に未定義の状態があるためです。 代わりに、次のように使用する必要があります。*「ビデオを再生」*、簡潔であり複数音節文字があります。
* 単純なボキャブラリを使用します。 常に共通の単語や語句を検出し、保存、ユーザーが容易であるを使用してください。 たとえば、アプリケーションに表示または非表示になりますが、注オブジェクトがある場合はいないコマンドを使用する *「プラカードを表示」*「プラカード」はめったに使用される用語であるためです。 代わりに、コマンドを使用します。*「メモを表示する」* アプリケーションの注意事項を表示します。
* 一貫性を保ちます。 音声コマンド、アプリケーション全体が一貫性のある保持される必要があります。 2 つのシーン、アプリケーションであり、その両方のシーンは、アプリケーションを終了するためのボタンを含めることが想像してみてください。 最初のシーンは、コマンドを使用する場合 *"Exit"* シーンがコマンドを使用する、ボタンが 2 番目のトリガーを *「アプリを閉じる」* ユーザーが混乱するからです。 複数のシーン間で同じ機能が解決しない場合、それをトリガーする同じ音声コマンドを使用する必要があります。

#### <a name="dont"></a>できません

* 1 つ音節コマンドを使用します。 例として、音声、ビデオを再生するコマンドを作成する場合を避ける必要があります、単純なコマンドを使用して *「再生」* 音節は 1 つのみであり、システムで簡単に見落とされる可能性があります。 代わりに、次のように使用する必要があります。*「ビデオを再生」*、簡潔であり複数音節文字があります。
* システムのコマンドを使用します。 *"Select"* コマンドは、現在フォーカスがあるオブジェクトのタップ イベントをトリガーする、システムによって予約されています。 再使用しない、 *"Select"* キーワードまたは語句のコマンドは期待どおりには動作しない可能性があります。 などの場合は、アプリケーションでキューブを選択するための音声コマンドが *「キューブの選択」* ユーザーが求めていた球体で、コマンドを載せた、ときに球は、代わりに、選択した後、します。 同様にアプリ バーのコマンドは、ボイスが有効になっています。 CoreWindow ビューでは、次のような音声コマンドを使用しません。
    1. 戻ってください
    2. スクロール ツール
    3. ズーム ツール
    4. ドラッグ ツール
    5. Adjust
    6. Remove
* ようなサウンドを使用します。 広げると覚える音声コマンドを使用しないようにしてください。 サポート ショッピング アプリケーションがあれば *「ストアの表示」* と *「詳細」* し、もう一方を使用していたときに、コマンドのいずれかを無効にすると、同様の音声コマンド。 たとえば、使用する可能性があります、 *「を表示する格納」* 、ストアを開くボタンをクリックし、ストアが表示されたときにそのコマンドを無効にできるように、 *「詳細」* コマンドが参照される可能性があります。

### <a name="instructions"></a>手順

* Unity の**階層**パネルで、検索する検索ツールを使用して、 **holoComm_screen_mesh**オブジェクト。
* ダブルクリックして、 **holoComm_screen_mesh**でそれを表示するオブジェクト、**シーン**します。 これは、「宇宙飛行士のウォッチ式は、音声コマンドに応答します。
* **インスペクター**パネルで、検索、**音声入力ソース (スクリプト)** コンポーネント。
* 展開、**キーワード**セクションには、サポートされている音声コマンド。**Communicator を開く**します。
* 右側にある歯車アイコンをクリックし、選択**スクリプトの編集**します。
* 探索**SpeechInputSource.cs**で使用する方法を理解する、 **KeywordRecognizer**音声コマンドを追加します。

### <a name="build-and-deploy"></a>構築し、デプロイ

* Unity では、次のように使用します。**ファイル > Build Settings** 、アプリケーションをリビルドします。
* 開く、**アプリ**フォルダー。
* 開く、 **ModelExplorer Visual Studio ソリューション**します。

(既にビルド/展開して Visual Studio では、このプロジェクトのセットアップ中に場合、し、VS のインスタンスを開いて 'すべて再読み込み' が表示されたらクリックします)。

* Visual Studio で、次のようにクリックします。**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。
* アプリケーションのデプロイは、HoloLens 後に、合わせる ボックスを使用して、閉じ、[エア タップ](gestures.md#air-tap)ジェスチャ。
* 「宇宙飛行士ウォッチを見つめます。
* ウォッチにフォーカスがある場合は、カーソルがマイクに変更されることを確認します。 これは、音声コマンドをアプリケーションがリッスンしてフィードバックを提供します。
* Watch でツールヒントが表示されることを確認します。 これにより、ユーザーの検出、 *"開いている Communicator"* コマンド。
* ウォッチで gazing、中に答えて *"開く Communicator"* communicator パネルを開きます。

## <a name="chapter-2---acknowledgement"></a>第 2 章 – 受信確認

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>目標

* マイクの入力を使用してメッセージを記録します。
* アプリケーションがそれぞれの声をリッスンしていることをユーザーにフィードバックを提供します。

>[!NOTE]
>**マイク**マイクから記録するアプリの機能を宣言する必要があります。 これを行うことを既に MR 入力 212、ただしこれ独自のプロジェクトに注意してください。
>
>1. Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」に移動して、player の設定に移動します。
>2. "ユニバーサル Windows プラットフォーム タブをクリックします。
>3. 「発行の設定 > 機能」セクションでは、確認、**マイク**機能

### <a name="instructions"></a>手順

* Unity の**階層**パネルで、ことを確認します、 **holoComm_screen_mesh**オブジェクトを選択します。
* **インスペクター**パネルで、検索、**飛行士ウォッチ (スクリプト)** コンポーネント。
* 値として設定されますが、小さな青いキューブをクリックして、 **Communicator Prefab**プロパティ。
* **プロジェクト**パネル、 **Communicator**プレハブはフォーカスがあるようになりました。
* をクリックして、 **Communicator**のプレハブ、**プロジェクト**でそのコンポーネントを表示するパネル、**インスペクター**します。
* 見て、**マイク マネージャー (スクリプト)** コンポーネント、これにより、ユーザーの音声を記録します。
* 注意、 **Communicator**オブジェクトには、**音声入力ハンドラー (スクリプト)** コンポーネントへの応答を**メッセージの送信**コマンド。
* 見て、 **Communicator (スクリプト)** コンポーネントと Visual Studio で開くスクリプトをダブルクリックします。

Communicator.cs は communicator のデバイスで適切なボタンの状態を設定します。 これによって、ユーザー メッセージを記録、再生、および、飛行士にメッセージを送信します。 開始もとそれぞれの声が聞こえたことをユーザーに確認をアニメーション化された波フォームを停止します。

* **Communicator.cs**から次の行 (81 および 82) を削除、**開始**メソッド。 これは、communicator の 'Record' ボタンを有効になります。

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>構築し、デプロイ

* Visual Studio で、アプリケーションをリビルドし、デバイスに展開します。
* 「宇宙飛行士ウォッチ見つめますと答えて *"開いている Communicator"* 、communicator を表示します。
* キーを押して、**レコード**口頭でメッセージを「宇宙飛行士記録を開始するボタン (マイク)。
* 、読み上げを開始し、wave アニメーションの再生、communicator では、ユーザーにフィードバックを提供するには、それぞれの声を聞いたことのことを確認します。
* キーを押して、**停止**(四角形の左) ボタンをクリックし、wave アニメーションが実行を停止していることを確認します。
* キーを押して、**再生** (直角三角形)、記録されたメッセージを再生し、デバイスをお待ちしております。
* キーを押して、**停止**ボタン (右の正方形)、記録されたメッセージの再生を停止します。
* たとえば *「メッセージの送信」* communicator を閉じてから、「宇宙飛行士 'メッセージが受信した' 応答を受信しますします。

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>第 3 章 - ディクテーション認識エンジンと理解

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>目標

* ディクテーション認識エンジンを使用して、ユーザーの音声をテキストに変換します。
* Communicator でディクテーション認識エンジンの仮説と最終的な結果を表示します。

この章でディクテーション認識エンジン、飛行士に対するメッセージの作成に使用します。 ディクテーション認識エンジンを使用する場合に注意します。

* 作業をディクテーション認識エンジンの WiFi に接続されている必要があります。
* タイムアウトは、一定期間の後に発生します。 注意すべき 2 つのタイムアウトがあります。
  * 認識エンジンが起動し、最初の 5 秒間のオーディオの声が場合、タイムアウトになります。
  * 認識エンジンが指定の結果を 20 秒の無音が場合がタイムアウトになります。
* (キーワードまたはディクテーション) 認識エンジンの 1 つだけの型は、いつでも実行できます。

>[!NOTE]
>**マイク**マイクから記録するアプリの機能を宣言する必要があります。 これを行うことを既に MR 入力 212、ただしこれ独自のプロジェクトに注意してください。
>
>1. Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」に移動して、player の設定に移動します。
>2. "ユニバーサル Windows プラットフォーム タブをクリックします。
>3. 「発行の設定 > 機能」セクションでは、確認、**マイク**機能

### <a name="instructions"></a>手順

編集しようとして**MicrophoneManager.cs**ディクテーション認識エンジンを使用します。 これは、追加します。

1. ときに、**録画ボタン**は、押された、 **、DictationRecognizer を開始**します。
2. 表示、**仮説**DictationRecognizer が認識されるのです。
3. 内のロック、**結果**DictationRecognizer が認識されるのです。
4. DictationRecognizer タイムアウトを確認します。
5. ときに、**停止ボタン**が押された mic セッションがタイムアウトまたは **、DictationRecognizer を停止**します。
6. 再起動、 **KeywordRecognizer**、リッスン、**メッセージの送信**コマンド。

それでは始めましょう。 3. a でのコーディングの練習をすべて完了**MicrophoneManager.cs**、またはコピーして、下の完成したコードを貼り付けます。

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone. 
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>構築し、デプロイ

* Visual Studio での再構築し、デバイスに展開します。
* エア タップ ジェスチャに合わせるボックスを閉じます。
* 「宇宙飛行士ウォッチ見つめますと答えて *"開いている Communicator"* します。
* 選択、**レコード**ボタン (マイク)、メッセージを記録します。
* 読み上げを開始します。 **ディクテーション認識エンジン**音声を解釈し、communicator の仮説のテキストを表示します。
* 格言をお試しください *「メッセージの送信」* メッセージを記録している間です。 注意、**キーワード認識エンジン**ために、応答しません、**ディクテーション認識エンジン**アクティブなままです。
* 数秒の読み上げを停止します。 観察ディクテーション認識エンジンがその仮説を完了して、最終的な結果を示しています。
* 読み上げを開始し、20 秒間一時停止します。 これにより、**ディクテーション認識エンジン**タイムアウトにします。
* 注意、**キーワード認識エンジン**が上記のタイムアウト後に再度有効にします。 Communicator は、音声コマンドに応答ようになりました。
* たとえば *「メッセージの送信」* 飛行士にメッセージを送信します。

## <a name="chapter-4---grammar-recognizer"></a>第 4 章 - 音声認識の文法

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>目標

* に従って SRGS、または音声認識文法仕様ファイルをユーザーの音声認識文法認識エンジンを使用します。

>[!NOTE]
>**マイク**マイクから記録するアプリの機能を宣言する必要があります。 これを行うことを既に MR 入力 212、ただしこれ独自のプロジェクトに注意してください。
>
>1. Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」に移動して、player の設定に移動します。
>2. "ユニバーサル Windows プラットフォーム タブをクリックします。
>3. 「発行の設定 > 機能」セクションでは、確認、**マイク**機能

### <a name="instructions"></a>手順

1. **階層**パネルで、検索**Jetpack_Center**して選択します。
2. 探して、**末尾アクション**でスクリプトを作成、**インスペクター**パネル。
3. 右側の小さな円をクリックして、**オブジェクトをタグに沿った**フィールド。
4. ウィンドウが表示されたら、検索**SRGSToolbox**し、一覧から選択します。
5. 見て、 **SRGSColor.xml**ファイル、 **StreamingAssets**フォルダー。
* SRGS の設計仕様は、W3C web サイトで確認できます[ここ](https://www.w3.org/TR/speech-grammar/)します。
* SRGS ファイルでは、次の 3 つの種類のルールがあります。
  * 12 個の色の一覧から 1 つの色とするルール。
  * 色のルールと 3 つの図形の 1 つの組み合わせをリッスンする 3 つの規則。
  * ルート ルールでは、colorChooser で、次の 3 つの「色 + 図形の」ルールの任意の組み合わせをリッスンします。 任意の順序で、どんな量の 3 つすべてを 1 つだけで、図形と言えます。 これは、最初にファイルの上部にあるルート規則として指定されているのルールのみが、リッスンが&lt;文法&gt;タグ。

### <a name="build-and-deploy"></a>構築し、デプロイ

* Unity では、アプリケーションをリビルドし、ビルド HoloLens でアプリを体験する Visual Studio からデプロイします。
* エア タップ ジェスチャに合わせるボックスを閉じます。
* 「宇宙飛行士の jetpack 見つめますとをエア タップ ジェスチャを実行します。
* 読み上げを開始します。 **文法レコグナイザー**音声を解釈し、認識に基づいて図形の色を変更します。 コマンドの例は、「青色、黄色の正方形」です。
* ツールボックスを消去する別のエア タップ ジェスチャを実行します。

## <a name="the-end"></a>最後です

これで終了です。 完了したので**MR 入力 212。音声**します。

* Dos および音声コマンドのすべきでないことを確認します。
* ユーザーに音声コマンドを認識するツールヒントが採用された方法を説明しました。
* 複数の種類のフィードバックを使用して、ユーザーの声が聞こえたのことを確認しました。
* キーワード認識とディクテーション認識エンジンを切り替える方法について説明し、これら 2 つの機能が理解し、音声を解釈する方法がわかります。
* アプリケーションで音声認識、SRGS ファイルと文法認識エンジンを使用する方法を学習しました。
