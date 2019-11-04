---
title: Azure Speech Services チュートリアル-2. 音声からテキストへのローカル翻訳のオフラインモードの追加
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 5382a1cce38e8607042c21b8dd3157d1da2fa72e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437557"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a>2. ローカルの音声テキスト翻訳のオフラインモードを追加する

このチュートリアルでは、Azure サービスに接続できない場合に、ローカルの音声からテキストへの変換を実行できるオフラインモードを追加します。 また、切断された状態を*シミュレート*します。

## <a name="instructions"></a>手順

1. 階層内の Lunarcom_Base オブジェクトを選択します。
2. [インスペクター] パネルの [コンポーネントの追加] をクリックします。 Lunarcom のオフライン認識を検索して選択します。

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

3. LunarcomOfflineRecognizer のドロップダウンをクリックし、[有効] を選択します。 このプログラムでは、ユーザーのように動作するプロジェクトは接続されていません。 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

4. Unity エディターで Play を押し、テストします。 シーンの左下隅にあるマイクを押し、読み上げを開始します。 

> [!NOTE]
> オフラインになっているため、復帰ワードの機能が無効になっています。 オフライン時に音声を認識させるには、マイクを物理的にクリックする必要があります。 

シーンの外観の例を次に示します。

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a>結論

オフラインモードが有効になっています。 これで、オフラインになっても、speech SDK を使用してプロジェクトを操作できます。 


[次のチュートリアル: 3. Azure Cognitive Services speech translation コンポーネントを追加する](mrlearning-speechSDK-ch3.md)

