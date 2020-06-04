---
title: 音声入力
description: HoloLens 2 および Unreal engine での音声入力の設定と使用に関するチュートリアル
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality、Unreal、Unreal Engine 4、UE4、HoloLens 2、音声、音声入力、音声認識、Mixed Reality、開発、機能、ドキュメント、ガイド、ホログラム、ゲーム開発
ms.openlocfilehash: c5de0cd912674ccd681fd398fb6fe5fd345ab6f2
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330634"
---
# <a name="voice-input-in-unreal"></a>Unreal での音声入力

## <a name="overview"></a>概要
音声入力を使用すると、ハンドジェスチャを使用しなくても、また HoloLens (第1世代) と HoloLens 2 でサポートされています。 これは、他のすべてのユニバーサル Windows アプリで音声をサポートするのと同じエンジンによって機能し、混合現実の対話方法に自然な感覚を追加することができます。 

サポートされている音声機能は次のとおりです。
- [Select コマンド](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)
- [Cortana さん、こんにちは](https://docs.microsoft.com/windows/mixed-reality/voice-input#hey-cortana)
- 「ボタンとラベルの相互作用」を参照してください。
- ディクテーション

詳細については、主な[音声入力](voice-input.md)のドキュメントを参照してください。

## <a name="enabling-speech-recognition"></a>音声認識を有効にする

HoloLens で音声認識を有効にするには:
1. [プロジェクトの設定] を選択して **> プラットフォーム > HoloLens > 機能**を選択し、**マイク**を有効にします。 
2. [設定] で音声認識を有効にしました。 **> プライバシー > 音声**で、[**英語**] を選択します。

> [!NOTE]
> 音声認識は常に、**設定**アプリで構成された Windows 表示言語で機能します。 また、サービス品質を最大限に高めるために、**オンライン音声認識**を有効にすることをお勧めします。

![Windows 音声認識の設定](images/unreal/speech-recognition-settings.png)

3. アプリケーションが最初にマイクを有効にするかどうかを確認すると、ダイアログが表示されます。 **[はい]** を選択すると、アプリで音声入力が開始されます。

音声入力には、特別な Windows Mixed Reality Api は必要ありません。これは、既存の Unreal Engine 4[入力](https://docs.unrealengine.com/Gameplay/Input/index.html)マッピング API を基に構築されています。 

## <a name="adding-speech-mappings"></a>音声マッピングの追加
音声入力を使用する場合は、音声をアクションに接続することが重要な手順です。 これらのマッピングは、ユーザーが話す可能性のある音声キーワードをアプリで監視し、リンクされたアクションを起動します。 音声マッピングは、次の方法で見つけることができます。
1. [**プロジェクト設定の編集 >**] を選択し、[**エンジン**] セクションまでスクロールして [**入力**] をクリックします。

ジャンプコマンドの新しい音声マッピングを追加するには、次のようにします。
1. [ **+** **配列要素**] の横にあるアイコンをクリックし、次の値を入力します。
    * **アクション名**の**jumpWord**
    * **Speech キーワード**の**ジャンプ**

> [!NOTE]
> すべての英語の単語または短い文をキーワードとして使用できます。 

![UE4 Engine 入力いいえ](images/unreal/engine-input.png)

音声マッピングは、アクションや軸のマッピングなどの入力コンポーネントとして、またはイベントグラフのブループリントノードとして使用できます。 たとえば、ジャンプコマンドをリンクして、単語が話されるタイミングに応じて2つの異なるログを出力することができます。

1. ブループリントをダブルクリックして、**イベントグラフ**で開きます。
2. **右クリック**して音声マッピングの**アクション名**(この場合は**jumpWord**) を検索し、 **enter キー**を押します。 これにより、グラフに**入力アクション**ノードが追加されます。
3. 次の図に示すように、**押さ**れた pin をドラッグアンドドロップして文字列ノードを**印刷**します。 **解放**された pin は空のままにすることができ、音声マッピングの場合は何も実行されません。
 
![音声の単純なアクション](images/unreal/voice-input-img-03.png)

4. アプリを再生します。 word の**ジャンプ**を言い、コンソールでログを出力します。

これで、HoloLens アプリへの音声入力の追加を開始する必要があります。 音声と対話機能の詳細については、以下のリンクを参照してください。ユーザー向けに作成しているエクスペリエンスについて考えてください。

## <a name="see-also"></a>関連項目
* [視線入力とコミット](gaze-and-commit.md)
* [本能的な操作](interaction-fundamentals.md)
* [MR 入力 212:音声](holograms-212.md)
