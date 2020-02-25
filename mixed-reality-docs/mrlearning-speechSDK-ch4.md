---
title: Azure Speech Services チュートリアル-4. インテントの設定と自然言語の理解
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 8805fa6410e882bce2f0fe8da780dfd5f794cc74
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554002"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. インテントと自然言語の理解の設定

このレッスンでは、Azure Speech Service のインテント機能について説明します。 インテント機能を使用すると、アプリケーションに AI を使用した音声コマンドが適用されます。ユーザーは、特定の音声コマンドではなく、システムによってその意図を理解できます。 このレッスンでは、Azure LUIS Portal を設定し、インテント/エンティティ/発話を設定し、インテントリソースを発行し、Unity アプリをインテントリソースに接続して、最初のインテント API 呼び出しを行います。

## <a name="objectives"></a>目標

- アプリケーションでインテントと自然言語の理解を設定する方法について説明します。
- Azure の LUIS ポータルを設定する方法について説明します。
- Azure でインテント、エンティティ、および発話を設定する方法について説明します

## <a name="instructions"></a>手順

1. コンピューターでディクテーションを有効にできるようにします。 これを行うには、[Windows の設定] にアクセスし、[プライバシー]、[音声] の順に選択し、[インク & 入力] をクリックして、音声サービスをオンにして、候補を入力します。

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. [Azure Portal](https://portal.azure.com/)にログインします。 ログインしたら、[リソースの作成] をクリックし、[Language Understanding] を検索して、Enter キーを押します。

    ![mrlearning-speech-ch4-1-step2](images/mrlearning-speech-ch4-1-step2.png)

3. このサービスのインスタンスを作成するには、 **[作成]** ボタンをクリックします。

    ![mrlearning-speech-ch4-1-step3a](images/mrlearning-speech-ch4-1-step3a.png)

    リソースに**名前**を付けます。たとえば、「 *Speech-SDK-Learning-Module*」と指定します。 **サブスクリプション**については、試用版アカウントをお持ちの場合は、*従量課金制*または*無料証跡*を選択します。 次に、 **[新規作成]** リンクをクリックして新しい**リソースグループ**を作成し、たとえば「 *HoloLens-2-チュートリアル-リソースグループ*」という名前を入力して、 **[OK]** ボタンをクリックします。

    ![mrlearning-speech-ch4-1-step3b](images/mrlearning-speech-ch4-1-step3b.png)

4. **作成場所**と**実行時の場所**を選択します。 このチュートリアルでは、[*米国西部*] を使用します。次に、 **[オーサリング価格レベル]** と **[ランタイム価格レベル]** に [ *F0] (1 秒あたり5回、1か月あたり10,000 回)* を選択します。 最後に、 **[作成]** ボタンをクリックして、新しいリソースグループだけでなく、リソースを作成します。

    ![mrlearning-speech-ch4-1-step4](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    >[作成] ボタンをクリックした後、サービスが作成されるまで待機する必要があります。これには数分かかる場合があります。

5. リソースの作成プロセスが完了すると、**デプロイが完了**したことを確認するメッセージが表示されます。

    ![mrlearning-speech-ch4-1-step5](images/mrlearning-speech-ch4-1-step5.png)

6. 同じユーザーアカウントを使用して、 [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/)ポータルにサインインし、お住まいの国を選択して、使用条件に同意します。

    >[!NOTE]
    >Language Understanding ポータルに達したら、Azure portal と同じ資格情報を使用してログインする必要がある場合があります (まだログインしていない場合)。 LUIS を初めて使用する場合は、[ようこそ] ページの一番下までスクロールして [Create LUIS] \ (アプリの作成 \) ボタンをクリックする必要があります。

7. ログインしたら、[マイアプリ] をクリックします (現在このセクションにない場合)。 [新しいアプリの作成] をクリックします。 新しいアプリに "Speech SDK Learning Module" という名前を指定します。 "Speech SDK Learning Module" を [説明] フィールドにも追加します。 [完了] をクリックします。

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    >アプリが英語とは異なる言語を認識する場合は、"Culture" を適切な言語に変更する必要があります。

8. 右上にある [ビルド] をクリックします。

9. 左側の [アプリ資産] で、[インテント] を選択し、[新しいインテントの作成] をクリックして、"PressButton" という名前を指定します。

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    >このチュートリアルで使用するインテントとエンティティの名前は、Lunarcom アプリが名前で参照するため、使用することが重要です。

    >[!NOTE]
    >これで、"PressButton" と "None" の2つのインテントが作成されました。

10. 左側の [アプリ資産] で、[エンティティ] を選択し、[新しいエンティティの作成] をクリックして、「アクション」という名前を付け、エンティティ型を "Simple" として保持します。

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. [新しいエンティティの作成] をもう一度クリックし、"Target" という名前を指定します。 エンティティ型も "Simple" として保持します。

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. 左側の [アプリ資産] で、[インテント] を選択し、手順 10. で作成した "PressButton" インテントをクリックします。

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. 右側の [表示オプション] ドロップダウンをクリックし、[エンティティ値の表示] を選択します。

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    [例を入力してください...] をクリックします。 ボックスに入力します。 次に、次の発話を入力します。

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. 右側の [表示オプション] ドロップダウンをクリックし、[エンティティ名の表示] を選択します。

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. 10の各発話に、次のエンティティラベルが1つずつ含まれていることを確認してください。)mislabeled の単語をクリックし、ポップアップで [ラベルの削除] と [2] を選択します。ラベルを付ける必要がある単語をクリックし、ポップアップで適切なラベルを選択します。

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. 次に、モデルを発行するために、右上にある [トレーニング] をクリックします。 次に、処理が完了したら、右上の [Test] \ (テスト \) をクリックします。

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. テキストボックスの [起動ボタンを選択してください] に「」と入力します。

    >[!NOTE]
    >発話のいずれかに "select" をアクションとして追加しませんでしたが、[検査] をクリックすると、モデルはアクションエンティティとして "select" を認識しました。
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. 右上にある [発行] をクリックします。 ドロップダウンが "Production" と表示されていることを確認し、ポップアップの [発行] をクリックします。

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. 発行されると、ページの上部に緑色のバーが表示されます。 緑色のバーをクリックすると、[管理] ページが表示されます。

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. 左側の [アプリケーションの設定] の下にある [キーとエンドポイント] をクリックします。 次に、ドロップダウンの [Publish To] を "Production" に設定します。 タイムゾーンを自分のものと一致するように設定し、チェックボックスをオンにしてすべての予測されたインテントスコアを含めます。 最後に、[リソースの割り当て] をクリックします。

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. 最初のドロップダウンから [テナント] を選択し、[サブスクリプション名] ボックスの一覧で [従量課金制] を選択します。 [LUIS リソース名] の下で、手順1-5 で作成したリソースを選択します。 次に、[リソースの割り当て] をクリックします。

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    >次のセクションで簡単にアクセスできるように、先ほど割り当てたリソースに関連付けられているエンドポイント URL をコピーして保存してください。

    >[!NOTE]
    >テナント名には、このアプリケーション用に作成した会社またはプロファイルを入力します。

22. 次に、Unity で新しいアプリを開き、階層内の Lunarcom_Base オブジェクトを選択します。 [インスペクター] パネルの [コンポーネントの追加] をクリックし、"LunarcomIntentRecognizer" を検索して選択します。

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. [インスペクター] パネルの [Luis Endpoint] フィールドに、手順21で保存したエンドポイント URL を入力します。

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    >[インスペクター] パネルの [LunarcomOfflineRecognizer] コンポーネントで、"disable" が "SimulateOfflineMode" に対して選択されていることを確認します。そうしないと、プログラムのテストは機能しません。

24. [プロジェクト] ウィンドウで、[アセット] > [MRTK] に移動します。チュートリアル。 GettingStarted Prefabs > RocketLauncher フォルダーで、RocketLauncher_Complete prefab を階層ウィンドウにドラッグし、Lunarcom_Base オブジェクトの前に配置します。

    ![Module4Chapter4step24im](images/module4chapter4step24im-missing01.png)

25. 階層 ウィンドウで Lunarcom_Base オブジェクトを選択し、Lunarcom インテントレコグナイザー (スクリプト) コンポーネントを見つけます。次に、RocketLauncher_Complete > ボタンオブジェクトを展開し、各ボタンオブジェクトを対応する旧暦ランチャーボタンに割り当てます。分野.

    ![Module4Chapter4step24im](images/module4chapter4step24im-missing02.png)

26. Unity エディターの [再生] ボタンをクリックし、[ロケット] ボタンをクリックして、インテント認識を開始します。 「Utter を選択する」という語句を選択します。

    >[!NOTE]
    >アプリは目的の関数を認識し、ロケットボタンをアクティブにしました。
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>結論

このレッスンでは、AI を使用した音声コマンドを追加する方法について学習しました。 これで、ユーザーが正確な音声コマンドを utter ない場合でも、プログラムはユーザーの意図を認識できるようになりました。
