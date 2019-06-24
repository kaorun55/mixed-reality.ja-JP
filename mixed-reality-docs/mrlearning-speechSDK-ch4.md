## <a name="lesson-4"></a><span data-ttu-id="6fe7d-101">レッスン 4</span><span class="sxs-lookup"><span data-stu-id="6fe7d-101">Lesson 4</span></span>

<span data-ttu-id="6fe7d-102">4 章では、音声サービスのインテント機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-102">In chapter 4, we will explore the Speech services Intent feature.</span></span> <span data-ttu-id="6fe7d-103">私たちは、Azure LUIS ポータルのセットアップ、インテント/エンティティ/発話をセットアップ、目的のリソースを公開、Unity アプリを目的としたリソースに接続および最初の目的とした API 呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-103">We will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

1. <span data-ttu-id="6fe7d-104">Windows の設定に移動し、「"、「読み上げ、」し、最後に"手描き入力機能プライバシー、」と入力」を選択し、音声認識サービスと、入力候補を有効に、ディクテーションを有効にするためにコンピューターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-104">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> <span data-ttu-id="6fe7d-108">注: Mac/Macbook でこれを行う方法については、次のようにクリックします。[ここ](linkgoeshere)します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-108">note: for information on how to do this on a Mac/Macbook, click [here](linkgoeshere).</span></span>

2. <span data-ttu-id="6fe7d-109">[Azure ポータル](https://portal.azure.com/) にログインします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-109">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="6fe7d-110">ログインした後は、"Language Understanding"を検索して、リソースの作成をクリックし、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-110">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="6fe7d-112">このサービスのインスタンスを作成する、作成ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-112">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="6fe7d-113">"Speech_SDK_Learning_Module"プロジェクトの名前を指定し、"従量課金制。"を選択します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-113">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="6fe7d-116">お住まいの地域を選択します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-116">Select your Region.</span></span>  <span data-ttu-id="6fe7d-117">このチュートリアルでは、"(米国) West US"を選択します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-117">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="6fe7d-118">価格レベルの"F0"を選択します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-118">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="6fe7d-119">これで、リソースを作成する「作成」(左下隅にある) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-119">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

   >  <span data-ttu-id="6fe7d-120">注:「作成」でクリックすると、サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-120">note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="6fe7d-121">通知は、リソースが作成されたら、ポータルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-121">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="6fe7d-122">この通知をクリックし、「リソースに移動します。」を選択します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-122">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="6fe7d-123">"LUIS API"サービスの"クイック スタート ページで、最初の手順に移動し、キーを取得する"、"および「キー」(もこれを行う青のハイパーリンクをクリックして「キー、」次の図に示すように) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-123">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="6fe7d-124">これが明らかに、サービスでは、「キー」</span><span class="sxs-lookup"><span data-stu-id="6fe7d-124">This will reveal your service, "Keys."</span></span> <span data-ttu-id="6fe7d-125">後で、アプリで使用できるように、キーの 1 つのコピーを保存します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-125">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="6fe7d-127">セクション 2 b [「クイック スタート」] ページに戻るには、LUIS アプリケーション内で、新しいサービスの作成に使用する web ページにリダイレクトされる「Language Understanding ポータル」(上の図に示すように) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-127">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="6fe7d-128">注:「Language Understanding ポータル」達した場合は、必要がありますにログインしていない場合に、既に、Azure portal と同じ資格情報で。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-128">note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="6fe7d-129">LUIS を使用して、初めての場合は、検索、"作成 LUIS"アプリのボタンをクリックして、ウェルカム ページの一番下までスクロールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-129">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="6fe7d-130">ログインすると、(ない場合そのセクションでは現在) マイ アプリ をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-130">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="6fe7d-131">新しいアプリの作成をクリックすることができます。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-131">You can then click on Create new app.</span></span> <span data-ttu-id="6fe7d-132">新しいアプリの名前を「Speech SDK ラーニング モジュール」</span><span class="sxs-lookup"><span data-stu-id="6fe7d-132">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="6fe7d-133">説明フィールドにも、「Speech SDK ラーニング モジュール」を追加します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-133">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="6fe7d-134">"Done"をクリック</span><span class="sxs-lookup"><span data-stu-id="6fe7d-134">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="6fe7d-137">注:アプリは、英語以外の言語を理解することになって場合、は、適切な言語"Culture"を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-137">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="6fe7d-138">右上にある「ビルド」をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-138">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="6fe7d-139">下、左上のアセットをアプリ、「目的」を選択し、「新しい目的の作成」 をクリックし、"PressButton"という名前</span><span class="sxs-lookup"><span data-stu-id="6fe7d-139">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="6fe7d-141">注: 名前でインテントと Lunarcom アプリに参照するがあるために、このチュートリアルで使用するエンティティの名前を使用することが重要です。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-141">note: it is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>  <span data-ttu-id="6fe7d-142">その他のプロジェクトでは、何を選択した名前付け規則を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-142">For other projects, naming conventions can be whatever you choose.</span></span> 
>
> <span data-ttu-id="6fe7d-143">注:"PressButton"および"None です"- 2 のインテントが作成されました。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-143">note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="6fe7d-144">下、左上のアセットをアプリ、「エンティティ」を選択し、"新しいエンティティの作成 をクリックします"Action"という名前を付けます、「簡単」としてエンティティ型を保持</span><span class="sxs-lookup"><span data-stu-id="6fe7d-144">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="6fe7d-146">「新しいエンティティの作成」をもう一度クリックします。「ターゲット」という名前し、も「簡単」としてエンティティ型を保持します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-146">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="6fe7d-148">下、左上のアセットをアプリ、「目的」を選択し、手順 10. で作成した"PressButton"目的にをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-148">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="6fe7d-150">右側の「オプションの表示」ドロップダウンをクリックし、「エンティティの値を表示します」を選択します</span><span class="sxs-lookup"><span data-stu-id="6fe7d-150">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="6fe7d-152">「例を入力します...」 をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-152">Click on the “Enter an example…”</span></span> <span data-ttu-id="6fe7d-153">テキスト ボックス。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-153">textbox.</span></span> <span data-ttu-id="6fe7d-154">次に、次の発話を入力します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-154">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="6fe7d-156">右側の「オプションの表示」ドロップダウンをクリックし、「エンティティ名を表示します」を選択します</span><span class="sxs-lookup"><span data-stu-id="6fe7d-156">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="6fe7d-158">10 のそれぞれを 1 つ、次の場所に次のエンティティのラベルがある発話します)。間違った単語と、ポップアップで、「ラベルを削除」と 2 を選択します。)単語にラベルを付ける必要がありますにし、適切なラベルを選択すると、ポップアップをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-158">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="6fe7d-160">ここで、モデルを公開するには、右上で"Train"をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-160">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="6fe7d-161">次に、処理が完了すると、右上に"Test"をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-161">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="6fe7d-163">テキスト ボックスで、"select の起動ボタン"に入力します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-163">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="6fe7d-164">注: を追加していません"select"、アクションとして、発話のいずれが、「検査」をクリックすると、モデルの選択 として認識操作エンティティ。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-164">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="6fe7d-166">ここで、右上の [発行] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-166">Now, click "publish" in the top right.</span></span> <span data-ttu-id="6fe7d-167">ドロップダウン リストは"Production"ことを確認し、ポップアップもには、[発行] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-167">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="6fe7d-169">公開されると、ページの上部にある緑色のバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-169">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="6fe7d-170">[管理] ページに移動する緑色のバーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-170">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="6fe7d-172">左側に「キーとエンドポイント」"アプリケーション設定 の下をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-172">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="6fe7d-173">次に、ドロップ ダウン「発行先」を「実稼働します」として設定します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-173">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="6fe7d-174">一致させます、タイム ゾーンを設定し、すべての予測インテント スコアを含める ボックスを確認します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-174">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="6fe7d-175">最後に、「割り当てリソースです」をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-175">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="6fe7d-177">最初のドロップダウンからテナントを選択し、サブスクリプション名のドロップダウン リストに「従量課金制」を選択します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-177">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="6fe7d-178">LUIS リソース名の下には、手順 1. ~ 5. で作成したリソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-178">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="6fe7d-179">クリックし、「割り当てリソースです」</span><span class="sxs-lookup"><span data-stu-id="6fe7d-179">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="6fe7d-181">注: コピーして、次のセクションを簡単にアクセスできるようにだけ割り当てたリソースに関連付けられたエンドポイントの URL を保存することを確認します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-181">note: ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="6fe7d-182">注: テナントの名前を会社またはこのアプリケーション用に作成したプロファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-182">note: for the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="6fe7d-183">ここで、Unity で新しいアプリを開きし、階層の Lunarcom_Base オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-183">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="6fe7d-184">インスペクター ウィンドウで"コンポーネントの追加 をクリックして、検索し、"LunarcomIntentRecognizer。"を選択します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-184">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="6fe7d-186">インスペクター ウィンドウで"LunarcomIntentRecognizer"のフィールドに Luis エンドポイント、22 の手順で保存したエンドポイントの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-186">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="6fe7d-188">注:インスペクター ウィンドウで"LunarcomOfflineRecognizer"コンポーネントで"SimulateOfflineMode"それ「を無効にする」が選択されて、テスト、プログラムは機能しませんすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-188">note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="6fe7d-189">Unity エディターでの再生ボタンを押すし、意図認識を開始するロケット ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-189">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="6fe7d-190">「Rocket の起動ボタンを選択します」という語句を話した</span><span class="sxs-lookup"><span data-stu-id="6fe7d-190">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="6fe7d-191">注:アプリでは、必要な関数を認識し、ロケット ボタンをアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-191">note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="6fe7d-193">結論</span><span class="sxs-lookup"><span data-stu-id="6fe7d-193">Congratulations</span></span>

<span data-ttu-id="6fe7d-194">正式には、speech SDK のプログラムから音声コマンドを追加する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-194">You officially learned how to add speech commands from the speech SDK program!</span></span> <span data-ttu-id="6fe7d-195">今すぐプログラムでは、バリアント型のすべての種類の音声コマンドを認識できます。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-195">Now your program can recognize speech commands of all kinds of variants.</span></span> <span data-ttu-id="6fe7d-196">テストを実行し、多少の楽しみをしました。</span><span class="sxs-lookup"><span data-stu-id="6fe7d-196">Test it out and have a little fun with it!</span></span>

[<span data-ttu-id="6fe7d-197">次のレッスン:Speech SDK レッスン 5</span><span class="sxs-lookup"><span data-stu-id="6fe7d-197">Next Lesson: Speech SDK Lesson 5</span></span>](placeholderlink)

