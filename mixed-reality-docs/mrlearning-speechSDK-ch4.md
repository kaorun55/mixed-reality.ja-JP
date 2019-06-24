## <a name="lesson-4"></a>レッスン 4

4 章では、音声サービスのインテント機能について説明します。 私たちは、Azure LUIS ポータルのセットアップ、インテント/エンティティ/発話をセットアップ、目的のリソースを公開、Unity アプリを目的としたリソースに接続および最初の目的とした API 呼び出しを行います。

1. Windows の設定に移動し、「"、「読み上げ、」し、最後に"手描き入力機能プライバシー、」と入力」を選択し、音声認識サービスと、入力候補を有効に、ディクテーションを有効にするためにコンピューターを使用できます。

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> 注: Mac/Macbook でこれを行う方法については、次のようにクリックします。[ここ](linkgoeshere)します。

2. [Azure ポータル](https://portal.azure.com/) にログインします。 ログインした後は、"Language Understanding"を検索して、リソースの作成をクリックし、enter キーを押します。

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. このサービスのインスタンスを作成する、作成ボタンを選択します。 "Speech_SDK_Learning_Module"プロジェクトの名前を指定し、"従量課金制。"を選択します。

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. お住まいの地域を選択します。  このチュートリアルでは、"(米国) West US"を選択します。 価格レベルの"F0"を選択します。 これで、リソースを作成する「作成」(左下隅にある) をクリックします。

   >  注:「作成」でクリックすると、サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

5. 通知は、リソースが作成されたら、ポータルに表示されます。 この通知をクリックし、「リソースに移動します。」を選択します。

6. "LUIS API"サービスの"クイック スタート ページで、最初の手順に移動し、キーを取得する"、"および「キー」(もこれを行う青のハイパーリンクをクリックして「キー、」次の図に示すように) をクリックします。 これが明らかに、サービスでは、「キー」 後で、アプリで使用できるように、キーの 1 つのコピーを保存します。

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. セクション 2 b [「クイック スタート」] ページに戻るには、LUIS アプリケーション内で、新しいサービスの作成に使用する web ページにリダイレクトされる「Language Understanding ポータル」(上の図に示すように) をクリックします。

> 注:「Language Understanding ポータル」達した場合は、必要がありますにログインしていない場合に、既に、Azure portal と同じ資格情報で。 LUIS を使用して、初めての場合は、検索、"作成 LUIS"アプリのボタンをクリックして、ウェルカム ページの一番下までスクロールする必要があります。

8. ログインすると、(ない場合そのセクションでは現在) マイ アプリ をクリックします。 新しいアプリの作成をクリックすることができます。 新しいアプリの名前を「Speech SDK ラーニング モジュール」 説明フィールドにも、「Speech SDK ラーニング モジュール」を追加します。 "Done"をクリック

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> 注:アプリは、英語以外の言語を理解することになって場合、は、適切な言語"Culture"を変更する必要があります。

9. 右上にある「ビルド」をクリックします。

10. 下、左上のアセットをアプリ、「目的」を選択し、「新しい目的の作成」 をクリックし、"PressButton"という名前 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> 注: 名前でインテントと Lunarcom アプリに参照するがあるために、このチュートリアルで使用するエンティティの名前を使用することが重要です。  その他のプロジェクトでは、何を選択した名前付け規則を指定できます。 
>
> 注:"PressButton"および"None です"- 2 のインテントが作成されました。

11. 下、左上のアセットをアプリ、「エンティティ」を選択し、"新しいエンティティの作成 をクリックします"Action"という名前を付けます、「簡単」としてエンティティ型を保持

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. 「新しいエンティティの作成」をもう一度クリックします。「ターゲット」という名前し、も「簡単」としてエンティティ型を保持します。

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. 下、左上のアセットをアプリ、「目的」を選択し、手順 10. で作成した"PressButton"目的にをクリックします。

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. 右側の「オプションの表示」ドロップダウンをクリックし、「エンティティの値を表示します」を選択します 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)「例を入力します...」 をクリックします。 テキスト ボックス。 次に、次の発話を入力します。 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. 右側の「オプションの表示」ドロップダウンをクリックし、「エンティティ名を表示します」を選択します

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. 10 のそれぞれを 1 つ、次の場所に次のエンティティのラベルがある発話します)。間違った単語と、ポップアップで、「ラベルを削除」と 2 を選択します。)単語にラベルを付ける必要がありますにし、適切なラベルを選択すると、ポップアップをクリックします。

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. ここで、モデルを公開するには、右上で"Train"をクリックします。 次に、処理が完了すると、右上に"Test"をクリックします。

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. テキスト ボックスで、"select の起動ボタン"に入力します。

> 注: を追加していません"select"、アクションとして、発話のいずれが、「検査」をクリックすると、モデルの選択 として認識操作エンティティ。
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. ここで、右上の [発行] をクリックします。 ドロップダウン リストは"Production"ことを確認し、ポップアップもには、[発行] をクリックします。 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. 公開されると、ページの上部にある緑色のバーが表示されます。  [管理] ページに移動する緑色のバーをクリックします。 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. 左側に「キーとエンドポイント」"アプリケーション設定 の下をクリックします。 次に、ドロップ ダウン「発行先」を「実稼働します」として設定します。 一致させます、タイム ゾーンを設定し、すべての予測インテント スコアを含める ボックスを確認します。 最後に、「割り当てリソースです」をクリックします。

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. 最初のドロップダウンからテナントを選択し、サブスクリプション名のドロップダウン リストに「従量課金制」を選択します。 LUIS リソース名の下には、手順 1. ~ 5. で作成したリソースを選択します。 クリックし、「割り当てリソースです」 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> 注: コピーして、次のセクションを簡単にアクセスできるようにだけ割り当てたリソースに関連付けられたエンドポイントの URL を保存することを確認します。
>
> 注: テナントの名前を会社またはこのアプリケーション用に作成したプロファイルを配置します。

23. ここで、Unity で新しいアプリを開きし、階層の Lunarcom_Base オブジェクトを選択します。 インスペクター ウィンドウで"コンポーネントの追加 をクリックして、検索し、"LunarcomIntentRecognizer。"を選択します。

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. インスペクター ウィンドウで"LunarcomIntentRecognizer"のフィールドに Luis エンドポイント、22 の手順で保存したエンドポイントの URL を入力します。 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  注:インスペクター ウィンドウで"LunarcomOfflineRecognizer"コンポーネントで"SimulateOfflineMode"それ「を無効にする」が選択されて、テスト、プログラムは機能しませんすることを確認します。 

25. Unity エディターでの再生ボタンを押すし、意図認識を開始するロケット ボタンをクリックします。 「Rocket の起動ボタンを選択します」という語句を話した

>  注:アプリでは、必要な関数を認識し、ロケット ボタンをアクティブ化します。
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>結論

正式には、speech SDK のプログラムから音声コマンドを追加する方法を学習しました。 今すぐプログラムでは、バリアント型のすべての種類の音声コマンドを認識できます。 テストを実行し、多少の楽しみをしました。

[次のレッスン:Speech SDK レッスン 5](placeholderlink)

