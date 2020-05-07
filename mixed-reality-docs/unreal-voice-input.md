---
title: 音声入力
description: 音声入力の使用方法について説明します。
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality、HoloLens
ms.openlocfilehash: d61a9f9d40c76c8872ff0a1b39d65f95ae88d2b7
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835319"
---
# <a name="voice-input"></a>音声入力

HoloLens で音声認識を有効にするには、開発者は、プロジェクト設定 > Platform > HoloLens > の機能を使用して、Unreal エディターで "マイク" を有効にする必要があります。 デバイスでは、[設定 > プライバシー > 音声認識] で音声認識が有効になっていて、英語も使用されている必要があります。

![Windows 音声認識の設定](images/unreal/speech-recognition-settings.png)

サービスの品質を最大限に高めるために、オンライン音声認識を有効にすることをお勧めします。 HoloLens での音声認識の技術的な詳細については、こちらを参照して[ください](voice-input.md)。

その後、アプリケーションを初めて起動したときのマイクの有効化に関するダイアログが表示されます。 ユーザーが [はい] を選択すると、アプリケーションは音声入力の取得を開始します。

音声入力には、特別な Windows Mixed Reality API は必要ありません。代わりに、既存の Unreal Engine 4 入力マッピング API を基に構築されています。 入力 API の使用方法の詳細については、こちらを参照して[ください](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)。

音声マッピングが、エンジンのバインドセクションに追加されました。アクションと軸マッピングの下に入力します。 

![UE4 Engine 入力いいえ](images/unreal/engine-input.png)
 
ワールド "jump" の監視を追加する例を次に示します。 すべての英語の単語または短い文を使用できます。 

プロジェクト設定を使用して音声マッピングを追加すると、次の例に示すように、開発者は標準の Unreal ロジックを使用して入力を処理できます。 
 
![音声の単純なアクション](images/unreal/input-action-bp.png)
