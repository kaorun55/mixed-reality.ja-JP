---
title: Azure Speech Services チュートリアル-3. Azure Cognitive Services speech translation コンポーネントの追加
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 490b9f6142208a190748b6d76c57be493172c1e5
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913201"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Azure Cognitive Services speech 変換コンポーネントを追加する

このチュートリアルでは、プロジェクトの Azure Cognitive Services Speech Translation コンポーネントについて説明し、3つの異なる言語に翻訳します。

## <a name="instructions"></a>手順

1. 階層内の Lunarcom_Base オブジェクトを選択し、[インスペクター] パネルの [コンポーネントの追加] をクリックします。 [Lunarcom Translation レコグナイザー] を検索して選択します。

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    オフラインモードシミュレーターを無効にします。

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    >前の図に示すように、オフラインモードシミュレーターが無効になっていることを確認してから、Speech SDK 変換プログラムをテストしてください。 を翻訳するには、インターネットに接続されている必要があります。

2. [Lunarcom 変換認識エンジン] のドロップダウンをクリックし、変換する言語を選択します。

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. 次に、アプリケーションを実行し、[サテライト] ボタンをクリックして変換をテストし、読み上げを開始します。 [サテライト] ボタンをもう一度クリックして、認識を停止します。 シーンがどのように表示されるかの例を次に示します。 [ターゲット言語] ドロップダウンの下にある言語を自由に変更し (上の図を参照)、他の言語への翻訳を調べることができます。

    シーンの外観の例を次に示します。

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>結論

これで、お客様のプロジェクトで、話す単語を複数の異なる言語に変換できるようになりました。 自由に言語を自由に試して、翻訳の精度をテストしてください。

[次のチュートリアル: 4. インテントと自然言語の理解の設定](mrlearning-speechSDK-ch4.md)
