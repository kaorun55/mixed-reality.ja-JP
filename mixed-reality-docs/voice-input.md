---
title: 音声入力
description: 音声入力は、HoloLens と Windows Mixed Reality イマーシブ ヘッドセットの中核となる入力です。 コマンド、ディクテーション、Cortana、音声を使用できます。
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv, voice, cortana, speech, input
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829953"
---
# <a name="voice-input"></a>音声入力

音声では、3 つのキー入力での HoloLens の形式の 1 つです。 ホログラムを使用することがなく直接コマンドできます[ジェスチャ](gestures.md)します。 単に[視線](gaze.md)ホログラムでと、コマンドを読み上げます。 音声入力には、ユーザーの意図を通信するために、自然な方法を指定できます。 音声はユーザーが 1 つのコマンドを使用して入れ子になったメニューを切り抜けることができるため、複雑なインターフェイスを通過するに特に適してします。

音声入力が搭載されています、[同じエンジン](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)他のすべてのユニバーサル Windows アプリに音声認識をサポートします。

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a>デバイスのサポート

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>音声入力</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>(マイク) を使って ✔️</td>
    </tr>
</table>

## <a name="the-select-command"></a>"Select"コマンド

具体的には、アプリに音声のサポートを追加、しなくてもユーザーは、ホログラムを"select"と答えるとするだけでアクティブ化することができます。 これは、動作は同じ、[エア タップ](gestures.md#air-tap)HoloLens、上の select ボタンを押して、 [HoloLens clicker](hardware-accessories.md#hololens-clicker)トリガーを押したり、 [Windows Mixed Reality アニメーション コント ローラー](motion-controllers.md). 音が聞こえるされ、"select"を含む確認として表示されるヒントを参照してください。 低電力キーワードの検出アルゴリズムでは"select"が有効になっているため、いつでもあなたの側に手を使用しても、最小限のバッテリ寿命の影響をいつでも記述することができます。

> [!NOTE]
> HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。

![選択範囲に音声コマンドを使用するには、"select"](images/kma-voice-select-00170-800px.png)<br>
*選択範囲に音声コマンドを使用するには、"select"*

## <a name="hey-cortana"></a>[コルタナさん]

コルタナさん」はいつでも、Cortana を起動することも言えます。 彼女に質問は彼女の続行またはという命令に与えることなど、表示されるまで待機する必要はありません"Hey Cortana、天気とは何ですか"。 として 1 つの文。 Cortana と何ができるかについての詳細については、単にもらいます。 たとえば「what can Hey Cortana と言ったでしょうか。」 機能し、推奨されるコマンドの一覧を彼女をプルします。 Cortana アプリになっている場合は、クリックすることも、**でしょうか。** このメニューを取得するサイドバー上のアイコン。

**HoloLens に固有のコマンド**
* 音声操作の項目
* 「家に帰る」または"の先頭へ移動"- の代わりに[ブルーム](gestures.md#bloom)に[[スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)
* "起動<app>"
* "移動<app>ここで"
* 「画像を撮影する」
* 「記録の開始」
* [記録を停止する]
* 「明るさを」
* 「明るさを下げる」
* 「の音量を上げる」
* 「の音量を下げる」
* 「ミュート」または「ミュートを解除」
* 「デバイスをシャット ダウン」
* [デバイスを再起動する]
* "スリープ状態に移動
* 「どのような時間は?」
* 「どのくらいのバッテリは残っているでしょうか。」
* "呼び出す<contact>"(HoloLens の Skype が必要)

## <a name="see-it-say-it"></a>「認識, に言って」

HoloLens がも言うことがどのような音声コマンド ボタンにラベル指示がユーザーの音声入力、モデルを「認識,」ということ」を持ちます。 たとえば、2D アプリを調べるときにユーザーには、世界中で、アプリの位置を調整して、アプリ バーに表示されている「調整」コマンドは、できるとします。

![2D アプリまたはホログラムを見ると、ユーザー、アプリの世界での位置を調整して、アプリ バーに表示されている「調整」コマンドと言いますできます。](images/microphone-600px.png)

アプリでは、この規則に従う、ときにユーザー簡単に理解できる何を言おうシステムを制御します。 ボタンに gazing 中に、これを補強、するために、ボタンは、ボイスが有効なし、「押す」ことを話すコマンドが表示される場合、その後話題になる「音声ドウェル」ツールヒントが表示されます。

![表示に言って、ボタンの下にコマンドが表示されます](images/voice-seeitsayit-600px.png)<br>
*ボタンの下に表示されるコマンド「に言ってを参照してください」*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>高速ホログラム操作の音声コマンド

さまざまな音声コマンドにすばやく操作タスクを実行するホログラム gazing 中に指定するとします。 これらの音声コマンドは、2D アプリだけでなく、世界中に配置した 3D オブジェクトで機能します。

**ホログラム操作コマンド**
* 私が発生します。
* 大きな |強化
* 小

## <a name="dictation"></a>ディクテーション

型指定ではなく[エア タップ](gestures.md#air-tap)、音声認識をアプリにテキストを入力する方が効率的にすることができます。 入力をユーザーには、少ない労力でこれが大幅に迅速に行えます。

![音声認識がマイク ボタンを選択して開始します。](images/micbuttonfordictation.png)<br>
*音声認識をキーボード上にあるマイク ボタンを選択して開始します。*

Holographic キーボードがアクティブで、いつでも入力する代わりにディクテーション モードに切り替えることができます。 開始するのには、テキスト入力ボックスの横のマイクを選択します。

## <a name="communication"></a>通信

処理オプションの HoloLens によって提供されるカスタマイズされたオーディオ入力を活用する必要があるアプリケーションは、さまざまなを理解しておく必要[オーディオ ストリーム カテゴリ](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)アプリを使用できます。 これらの 3 つのいくつかの別のストリームのカテゴリと HoloLens では、Windows 10 のサポートを使用して、音声、通信、およびその他に使用できるオーディオのアンビエント環境に合わせたマイクのオーディオの品質を最適化するためにカスタム処理を有効にするにはキャプチャ (つまり"camcorder") のシナリオ。
* AudioCategory_Communications ストリーム カテゴリの呼び出しの品質とナレーションのシナリオ用にカスタマイズされた、ユーザーの声の 16 kHz 24 ビットのモノラル オーディオ ストリームをクライアントに提供
* AudioCategory_Speech ストリーム カテゴリでは、HoloLens (Windows) の音声認識エンジン用にカスタマイズされた、ユーザーの声の 16 kHz 24 ビット mono ストリームが提供されます。 このカテゴリは、必要な場合は、サード パーティの音声認識エンジンによって使用できます。
* AudioCategory_Other ストリーム カテゴリでは、オーディオ録音のアンビエント環境用にカスタマイズされた、48 kHz 24 ビットのステレオ オーディオ ストリームをクライアントに提供します。

このオーディオのすべての処理は、ハードウェア アクセラレーション機能は、ドレイン、HoloLens CPU 上で同じ処理が行った場合よりも大幅 power つまりです。 その他のオーディオの入力をシステムのバッテリ寿命を最大化し、組み込みの利用、CPU 上で処理を実行しないように、オーディオ入力の処理をオフロードします。

## <a name="troubleshooting"></a>トラブルシューティング

コルタナさん」、"select"を使用して問題が生じる場合は、ノイズ、または大きな声で話すことによって、ソースから離れた場所にすると、静か空間に移動してみてください。 現時点では、HoloLens のすべての音声認識はチューニングし、米国英語を母国に特に最適化します。

Windows Mixed Reality Developer Edition リリース 2017 では、オーディオ エンドポイント管理のロジックが数列 (無限) 後、最初のッドマウント接続後に PC のデスクトップ アウトされ、ログ記録します。 その最初の兆候アウト/経由 WMR OOBE 後のイベントで、前に、ユーザーから音声の入っていない切り替え、システムが、ッドマウントを最初に接続する前に設定する方法に応じて音声の入っていないまでさまざまなのオーディオ機能問題が発生する可能性があります。

## <a name="see-also"></a>関連項目
* [DirectX の音声入力](voice-input-in-directx.md)
* [Unity の音声入力](voice-input-in-unity.md)
* [MR 入力 212:音声](holograms-212.md)
