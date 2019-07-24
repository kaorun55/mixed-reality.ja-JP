---
title: 音声入力
description: 音声入力は、HoloLens および Windows Mixed Reality イマーシブヘッドセットの中核となる入力です。 音声は、コマンド、ディクテーション、Cortana などに使用できます。
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv、音声、cortana、音声、入力
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829953"
---
# <a name="voice-input"></a>音声入力

Voice は、HoloLens での3つの主要な入力形式の1つです。 これにより、[ジェスチャ](gestures.md)を使用せずに、ホログラムに直接コマンドを実行できます。 ホログラムを[見つめ](gaze.md)て、コマンドを話すだけです。 音声入力は、意図したとおりに通信するための自然な方法である可能性があります。 複雑なインターフェイスを走査するのは、ユーザーが1つのコマンドで入れ子になったメニューを使用できるようにするため、音声は特に便利です。

音声入力は、他のすべてのユニバーサル Windows アプリで音声をサポートするのと[同じエンジン](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)によって機能します。

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
        <td>✔️ (マイクを使用)</td>
    </tr>
</table>

## <a name="the-select-command"></a>"Select" コマンド

特に音声サポートをアプリに追加しなくても、ユーザーは "select" と言って、ホログラムをアクティブにすることができます。 これは、HoloLens での[エアタップ](gestures.md#air-tap)と同じように動作します。また、 [hololens clicker](hardware-accessories.md#hololens-clicker)の [選択] ボタンを押すか、 [Windows Mixed Reality モーションコントローラー](motion-controllers.md)でトリガーを押します。 サウンドが聞こえ、[選択] というヒントが確認として表示されます。 "Select" は、低電力キーワード検出アルゴリズムによって有効にされているため、ユーザー側でも、バッテリ寿命の影響を最小限に抑えていつでもいつでも使用できます。

> [!NOTE]
> HoloLens 2 に固有のその他のガイダンスは[近日対応予定](index.md#news-and-notes)です。

![選択に音声コマンドを使用するには、[選択] を言います。](images/kma-voice-select-00170-800px.png)<br>
*選択に音声コマンドを使用するには、[選択] を言います。*

## <a name="hey-cortana"></a>[コルタナさん]

また、いつでも cortana を立ち上げることができます。 自分の質問を続けたり、指示を与えたりすることができるようになるまで待つ必要はありません。たとえば、「Cortana はどうでしょうか。」と言ってください。 1つの文として。 Cortana とその対処方法の詳細については、 「Cortana が何を言うことができるか」と言ってください。 次に、作業と推奨されるコマンドの一覧を取得します。 既に Cortana アプリを使用している場合は、[?] をクリックすることもでき**ます。** 同じメニューをプルするためのサイドバーのアイコン。

**HoloLens 固有のコマンド**
* 音声操作の項目
* [[スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)を表示するには、[ブルーム](gestures.md#bloom)の代わりに [ホーム] または [スタートに移動] を実行します。
* "起動<app>"
* "ここ<app>に移動"
* "写真を撮る"
* "記録の開始"
* "記録の停止"
* 「明るさを上げる」
* 「明るさを下げる」
* "ボリュームを増やす"
* "音量を下げる"
* "ミュート" または "ミュート解除"
* "デバイスをシャットダウンする"
* "デバイスを再起動する"
* "スリープ状態に移行"
* "どのような時間がかかりますか。"
* 「どのくらいのバッテリが残っていますか?」
* "通話<contact>" (Skype for HoloLens が必要)

## <a name="see-it-say-it"></a>「言ってください。

HoloLens には、音声入力用の "it it はこれを見る" モデルがあります。ボタンのラベルはユーザーに対して、どのような音声コマンドを伝えることもできます。 たとえば、2D アプリを見ると、ユーザーはアプリバーに表示される "調整" コマンドを使用して、世界中のアプリの位置を調整することができます。

![2D アプリまたはホログラムを見ると、ユーザーはアプリバーに表示される "調整" コマンドを使用して、世界中のアプリの位置を調整することができます。](images/microphone-600px.png)

アプリがこの規則に従うと、ユーザーはシステムを制御する方法を簡単に理解できます。 これを補強するために、ボタンをクリックすると、ボタンが音声に対応している場合は1秒後に表示される "voice 熟考" というツールヒントが表示され、"press" を押すコマンドが表示されます。

![ボタンの下にコマンドが表示されるとします。](images/voice-seeitsayit-600px.png)<br>
*「これを見ると、ボタンの下にコマンドが表示される*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>迅速なホログラム操作のための音声コマンド

また、ホログラムを使用して操作を簡単に実行できる音声コマンドも多数あります。 これらの音声コマンドは、世界中に配置した3D オブジェクトだけでなく、2D アプリでも機能します。

**ホログラム操作コマンド**
* 顔
* 大規模 |用
* 小

## <a name="dictation"></a>ディクテーション

音声ディクテーションで入力するのでは[なく、アプリケーション](gestures.md#air-tap)にテキストを入力する方が効率的です。 これにより、ユーザーの負担を軽減しながら、入力を大幅に高速化できます。

![音声ディクテーションを開始するには、マイクボタンを選択します。](images/micbuttonfordictation.png)<br>
*音声ディクテーションを開始するには、キーボードのマイクボタンを選択します。*

Holographic キーボードがアクティブなときはいつでも、入力せずにディクテーションモードに切り替えることができます。 開始するには、テキスト入力ボックスの横にあるマイクを選択します。

## <a name="communication"></a>通信

HoloLens が提供するカスタマイズされたオーディオ入力処理オプションを利用する必要があるアプリケーションでは、アプリが使用できるさまざまな[オーディオストリームのカテゴリ](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)を理解することが重要です。 Windows 10 では、さまざまなストリームカテゴリがサポートされています。 HoloLens では、これらのうちの3つを使用して、音声、通信、およびアンビエント環境のオーディオ用に調整されたマイクオーディオの品質を最適化するカスタム処理を可能にします。キャプチャ ("カムコーダー" など) シナリオ。
* AudioCategory_Communications stream カテゴリは、通話の品質とナレーションのシナリオに合わせてカスタマイズされ、クライアントにユーザーの声の 16kHz 24bit mono オーディオストリームを提供します。
* AudioCategory_Speech stream カテゴリは、HoloLens (Windows) 音声エンジン用にカスタマイズされており、ユーザーの声の 16kHz 24bit mono ストリームを提供します。 このカテゴリは、サードパーティの音声エンジンで必要に応じて使用できます。
* AudioCategory_Other stream カテゴリはアンビエント環境オーディオ記録用にカスタマイズされており、クライアントには 48 Khz 24 ビットのステレオオーディオストリームが用意されています。

このようなオーディオ処理はすべてハードウェアアクセラレータです。これは、HoloLens CPU で同じ処理が行われた場合と比べて、機能の電力消費が多くなることを意味します。 システムのバッテリ寿命を最大化し、組み込みのオフロードオーディオ入力処理を活用するために、CPU で他のオーディオ入力処理を実行しないようにします。

## <a name="troubleshooting"></a>トラブルシューティング

"Select" と "Cortana" を使用して問題が発生している場合は、静かな領域に移動するか、ノイズの発生源から離れるか、音を大きくしてみてください。 現時点では、HoloLens の音声認識はすべて米国英語のネイティブスピーカーに対して調整および最適化されています。

Windows Mixed Reality Developer Edition release 2017 では、オーディオエンドポイント管理ロジックは、最初の HMD 接続の後、いったんログアウトして PC デスクトップに戻すと、正常に機能します。 ユーザーは、WMR OOBE を通過した後に初めてサインアウト/イベントが発生する前に、HMD を初めて接続する前にシステムがどのように設定されているかによって、オーディオの切り替えなしのさまざまなオーディオ機能の問題が発生する可能性があります。

## <a name="see-also"></a>関連項目
* [DirectX の音声入力](voice-input-in-directx.md)
* [Unity の音声入力](voice-input-in-unity.md)
* [MR 入力 212:音声](holograms-212.md)
