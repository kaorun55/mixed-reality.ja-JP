---
title: Azure Speech Services チュートリアル-4. インテントの設定と自然言語の理解
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 5ca2df56eee3ae41d97de4e8b1e88a39d4d36718
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701946"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4。インテントの設定と自然言語の理解

このレッスンでは、Azure Speech Service のインテント機能について説明します。 インテント機能を使用すると、アプリケーションに AI を使用した音声コマンドを提供できるようになります。この場合、ユーザーは特に特定できない音声コマンドを読み上げ、システムがその意図を理解することができます。 このレッスンでは、Azure LUIS Portal を設定し、インテント/エンティティ/発話を設定し、インテントリソースを発行し、Unity アプリをインテントリソースに接続して、最初のインテント API 呼び出しを行います。

## <a name="objectives"></a>目的

- アプリケーションでインテントと自然言語の理解を設定する方法について説明します。
- Azure の LUIS ポータルを設定する方法について説明します。
- Azure でインテント、エンティティ、および発話を設定する方法について説明します

## <a name="instructions"></a>手順
1. コンピューターでディクテーションを有効にするには、この操作を行うには、[Windows の設定] にアクセスし、[プライバシー]、[& 音声] の順に選択して、音声サービスをオンにして、候補を入力します。

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. [Azure ポータル](https://portal.azure.com/) にログインします。 ログインしたら、[リソースの作成] をクリックし、[Language Understanding] を検索して、enter キーを押します。

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. このサービスのインスタンスを作成するには、[作成] ボタンを選択します。 プロジェクトに "Speech_SDK_Learning_Module" という名前を付け、[従量課金制] を選択します。

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. リージョンを選択します。  このチュートリアルでは、[米国西部] を選択します。 次に、価格レベルとして "F0" を選択します。 次に、(左下隅にある) [作成] をクリックして、リソースを作成します。

>  注: [作成] をクリックすると、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

5. リソースが作成されると、ポータルに通知が表示されます。 この通知をクリックし、[リソースへのアクセス] を選択します。

6. "LUIS API" サービスの [クイックスタート] ページで、最初の手順に移動し、[キー] をクリックして、[キー] をクリックします (次の図に示されている青いハイパーリンク "キー" をクリックして、これを実現することもできます)。 これにより、サービス "キー" が表示されます。 アプリで後で使用できるように、いずれかのキーのコピーを保存します。

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. セクション2b の下にある [クイックスタート] ページに戻り、[Language Understanding ポータル] (上の図を参照) をクリックして、LUIS アプリケーション内で新しいサービスの作成に使用する web ページにリダイレクトします。

> 注:"Language Understanding ポータル" に到達した場合は、Azure portal と同じ資格情報を使用してログインする必要があります (まだログインしていない場合)。 LUIS を初めて使用する場合は、[ようこそ] ページの一番下までスクロールして、[Create LUIS] \ (アプリの作成 \) ボタンを見つけてクリックする必要があります。

8. ログインしたら、[マイアプリ] をクリックします (現在このセクションにない場合)。 [新しいアプリの作成] をクリックします。 新しいアプリに "Speech SDK Learning Module" という名前を指定します。 "Speech SDK Learning Module" を [説明] フィールドにも追加します。 [完了] をクリックします。

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> 付箋アプリが英語とは異なる言語を認識する場合は、"Culture" を適切な言語に変更する必要があります。

9. 右上にある [ビルド] をクリックします。

10. 左側の [アプリ資産] で、[インテント] を選択し、[新しいインテントの作成] をクリックして、"PressButton" という名前を指定します。 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> 注:このチュートリアルで使用するインテントとエンティティの名前は、Lunarcom アプリが名前で参照するため、使用することが重要です。 
>
> 注: "PressButton" と "None" の2つのインテントがあることに注意してください。

11. 左側の [アプリ資産] で、[エンティティ] を選択し、[新しいエンティティの作成] をクリックして、"Action" という名前を付け、エンティティ型を "Simple" にしておきます。

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. [新しいエンティティの作成] をもう一度クリックし、"Target" という名前を付けて、エンティティ型を "Simple" として保持します。

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. 左側の [アプリ資産] で、[インテント] を選択し、手順 10. で作成した "PressButton" インテントをクリックします。

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. 右側の [表示オプション] ドロップダウンをクリックし、[エンティティ値の表示] を選択します。 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)[例を入力してください...] をクリックします。 wl. 次に、次の発話を入力します。 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. 右側の [表示オプション] ドロップダウンをクリックし、[エンティティ名の表示] を選択します。

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. 10の各発話に、次のエンティティラベルが1つずつ含まれていることを確認してください。)mislabeled の単語をクリックし、ポップアップで [ラベルの削除] と [2] を選択します。ラベルを付ける必要がある単語をクリックし、ポップアップで適切なラベルを選択します。

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. 次に、モデルを発行するために、右上にある [トレーニング] をクリックします。 次に、処理が完了したら、右上の [Test] \ (テスト \) をクリックします。

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. テキストボックスの [起動ボタンを選択してください] に「」と入力します。

> 注: 発話のいずれかに "select" をアクションとして追加しませんでした。ただし、[検査] をクリックすると、モデルはアクションエンティティとして "select" を認識しました。
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. 次に、右上にある [発行] をクリックします。 ドロップダウンが "Production" と表示されていることを確認し、ポップアップの [発行] もクリックします。 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. 発行されると、ページの上部に緑色のバーが表示されます。  緑色のバーをクリックして、[管理] ページに移動します。 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. 左側の [アプリケーションの設定] の下にある [キーとエンドポイント] をクリックします。 次に、ドロップダウンの [Publish To] を "Production" に設定します。 タイムゾーンを自分のものと一致するように設定し、チェックボックスをオンにしてすべての予測されたインテントスコアを含めます。 最後に、[リソースの割り当て] をクリックします。

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. 最初のドロップダウンから [テナント] を選択し、[サブスクリプション名] ボックスの一覧で [従量課金制] を選択します。 [LUIS リソース名] の下で、手順1-5 で作成したリソースを選択します。 次に、[リソースの割り当て] をクリックします。 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> 注:次のセクションで簡単にアクセスできるように、先ほど割り当てたリソースに関連付けられているエンドポイント URL をコピーして保存してください。
>
> 注:テナント名には、このアプリケーション用に作成した会社またはプロファイルを入力します。

23. 次に、Unity で新しいアプリを開き、階層内の Lunarcom_Base オブジェクトを選択します。 [インスペクター] パネルの [コンポーネントの追加] をクリックし、"LunarcomIntentRecognizer" を検索して選択します。

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. [インスペクター] パネルの [Luis Endpoint] フィールドに、手順 22. で保存したエンドポイント URL を入力します。 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  注:[インスペクター] パネルの [LunarcomOfflineRecognizer] コンポーネントで、"disable" が "SimulateOfflineMode" に対して選択されていることを確認します。そうしないと、プログラムのテストは機能しません。 

25. Unity エディターの [再生] ボタンをクリックし、[ロケット] ボタンをクリックして、インテント認識を開始します。 「Utter を選択する」という語句を選択します。

>  注:アプリは目的の関数を認識し、ロケットボタンをアクティブにしました。
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>結論

このレッスンでは、AI を利用した音声コマンドを追加する方法について学習しました。 これで、ユーザーが正確な音声コマンドを utter ない場合でも、プログラムはユーザーの意図を認識できるようになりました。

