---
title: Azure Speech Services チュートリアル-3. Azure Cognitive Services speech translation コンポーネントの追加
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: c7cbdca3c22253042a9be44a194fca8925f0f446
ms.sourcegitcommit: 599bbdd861ce6ff11b6cfb345a0a995f8b7bf85b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68977959"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3.Azure Cognitive Services speech translation コンポーネントの追加

このチュートリアルでは、プロジェクトの Azure Cognitive Services Speech Translation コンポーネントについて説明し、3つの異なる言語に翻訳します。 

## <a name="instructions"></a>手順

1. 階層内の Lunarcom_Base オブジェクトを選択し、[インスペクター] パネルの [コンポーネントの追加] をクリックします。 LunarcomTranslationRecognizer を検索して選択します。

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> 注:Speech SDK 変換プログラムをテストする前に、オフラインモードシミュレーターが無効になっていることを確認します。 を翻訳するには、インターネットに接続されている必要があります。 この設定の場所については、下の画像を参照してください。 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. LunarcomTranslationRecognizer のドロップダウンをクリックし、翻訳する言語を選択します。

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. 次に、アプリケーションを実行し、[サテライト] ボタンをクリックして変換をテストし、読み上げを開始します。 [サテライト] ボタンをもう一度クリックして、認識を停止します。 シーンがどのように表示されるかの例を次に示します。 [ターゲット言語] ドロップダウンの下にある言語を自由に変更し (上の図を参照)、他の言語への翻訳を調べることができます。

> 注:テストする前に、次の図に示すように、オフラインシミュレーターが無効になっていることを確認します。
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

シーンの外観の例を次に示します。

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>結論

これで、お客様のプロジェクトで、話す単語を複数の異なる言語に変換できるようになりました。 自由に言語を自由に試して、翻訳の精度をテストしてください。 

[次のチュートリアル:4。インテントの設定と自然言語の理解](mrlearning-speechSDK-ch4.md)

