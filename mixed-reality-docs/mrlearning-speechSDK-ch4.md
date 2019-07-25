---
title: MR Learning SpeechSDK モジュール-音声認識と議事録
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 0cffb9ac8f61f77b77fc5925264b95ba57d94ece
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460346"
---
# <a name="speech-sdk-learning-module---intent-and-natural-language-understanding"></a><span data-ttu-id="423af-104">Speech SDK Learning モジュール-インテントと自然 Language Understanding</span><span class="sxs-lookup"><span data-stu-id="423af-104">Speech SDK Learning Module - Intent and Natural Language Understanding</span></span>

<span data-ttu-id="423af-105">このレッスンでは、Azure Speech Service のインテント機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="423af-105">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="423af-106">インテント機能を使用すると、アプリケーションに AI を使用した音声コマンドを提供できるようになります。この場合、ユーザーは特に特定できない音声コマンドを読み上げ、システムがその意図を理解することができます。</span><span class="sxs-lookup"><span data-stu-id="423af-106">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="423af-107">このレッスンでは、Azure LUIS Portal を設定し、インテント/エンティティ/発話を設定し、インテントリソースを発行し、Unity アプリをインテントリソースに接続して、最初のインテント API 呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="423af-107">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="423af-108">目的</span><span class="sxs-lookup"><span data-stu-id="423af-108">Objectives</span></span>

- <span data-ttu-id="423af-109">アプリケーションでインテントと自然言語の理解を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="423af-109">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="423af-110">Azure の LUIS ポータルを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="423af-110">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="423af-111">Azure でインテント、エンティティ、および発話を設定する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="423af-111">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="423af-112">手順</span><span class="sxs-lookup"><span data-stu-id="423af-112">Instructions</span></span>
1. <span data-ttu-id="423af-113">コンピューターでディクテーションを有効にするには、この操作を行うには、[Windows の設定] にアクセスし、[プライバシー]、[& 音声] の順に選択して、音声サービスをオンにして、候補を入力します。</span><span class="sxs-lookup"><span data-stu-id="423af-113">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. <span data-ttu-id="423af-117">[Azure ポータル](https://portal.azure.com/) にログインします。</span><span class="sxs-lookup"><span data-stu-id="423af-117">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="423af-118">ログインしたら、[リソースの作成] をクリックし、[Language Understanding] を検索して、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="423af-118">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="423af-120">このサービスのインスタンスを作成するには、[作成] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-120">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="423af-121">プロジェクトに "Speech_SDK_Learning_Module" という名前を付け、[従量課金制] を選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-121">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="423af-124">リージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-124">Select your Region.</span></span>  <span data-ttu-id="423af-125">このチュートリアルでは、[米国西部] を選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-125">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="423af-126">次に、価格レベルとして "F0" を選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-126">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="423af-127">次に、(左下隅にある) [作成] をクリックして、リソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="423af-127">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

>  <span data-ttu-id="423af-128">注: [作成] をクリックすると、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="423af-128">Note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="423af-129">リソースが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="423af-129">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="423af-130">この通知をクリックし、[リソースへのアクセス] を選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-130">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="423af-131">"LUIS API" サービスの [クイックスタート] ページで、最初の手順に移動し、[キー] をクリックして、[キー] をクリックします (次の図に示されている青いハイパーリンク "キー" をクリックして、これを実現することもできます)。</span><span class="sxs-lookup"><span data-stu-id="423af-131">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="423af-132">これにより、サービス "キー" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="423af-132">This will reveal your service, "Keys."</span></span> <span data-ttu-id="423af-133">アプリで後で使用できるように、いずれかのキーのコピーを保存します。</span><span class="sxs-lookup"><span data-stu-id="423af-133">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="423af-135">セクション2b の下にある [クイックスタート] ページに戻り、[Language Understanding ポータル] (上の図を参照) をクリックして、LUIS アプリケーション内で新しいサービスの作成に使用する web ページにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="423af-135">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="423af-136">注:"Language Understanding ポータル" に到達した場合は、Azure portal と同じ資格情報を使用してログインする必要があります (まだログインしていない場合)。</span><span class="sxs-lookup"><span data-stu-id="423af-136">Note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="423af-137">LUIS を初めて使用する場合は、[ようこそ] ページの一番下までスクロールして、[Create LUIS] \ (アプリの作成 \) ボタンを見つけてクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="423af-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="423af-138">ログインしたら、[マイアプリ] をクリックします (現在このセクションにない場合)。</span><span class="sxs-lookup"><span data-stu-id="423af-138">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="423af-139">[新しいアプリの作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="423af-139">You can then click on Create new app.</span></span> <span data-ttu-id="423af-140">新しいアプリに "Speech SDK Learning Module" という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="423af-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="423af-141">"Speech SDK Learning Module" を [説明] フィールドにも追加します。</span><span class="sxs-lookup"><span data-stu-id="423af-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="423af-142">[完了] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="423af-142">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="423af-145">付箋アプリが英語とは異なる言語を認識する場合は、"Culture" を適切な言語に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="423af-145">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="423af-146">右上にある [ビルド] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="423af-146">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="423af-147">左側の [アプリ資産] で、[インテント] を選択し、[新しいインテントの作成] をクリックして、"PressButton" という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="423af-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="423af-149">注:このチュートリアルで使用するインテントとエンティティの名前は、Lunarcom アプリが名前で参照するため、使用することが重要です。</span><span class="sxs-lookup"><span data-stu-id="423af-149">Note: It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span> 
>
> <span data-ttu-id="423af-150">注: "PressButton" と "None" の2つのインテントがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="423af-150">Note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="423af-151">左側の [アプリ資産] で、[エンティティ] を選択し、[新しいエンティティの作成] をクリックして、"Action" という名前を付け、エンティティ型を "Simple" にしておきます。</span><span class="sxs-lookup"><span data-stu-id="423af-151">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="423af-153">[新しいエンティティの作成] をもう一度クリックし、"Target" という名前を付けて、エンティティ型を "Simple" として保持します。</span><span class="sxs-lookup"><span data-stu-id="423af-153">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="423af-155">左側の [アプリ資産] で、[インテント] を選択し、手順 10. で作成した "PressButton" インテントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="423af-155">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="423af-157">右側の [表示オプション] ドロップダウンをクリックし、[エンティティ値の表示] を選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-157">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="423af-159">[例を入力してください...] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="423af-159">Click on the “Enter an example…”</span></span> <span data-ttu-id="423af-160">wl.</span><span class="sxs-lookup"><span data-stu-id="423af-160">textbox.</span></span> <span data-ttu-id="423af-161">次に、次の発話を入力します。</span><span class="sxs-lookup"><span data-stu-id="423af-161">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="423af-163">右側の [表示オプション] ドロップダウンをクリックし、[エンティティ名の表示] を選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-163">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="423af-165">10の各発話に、次のエンティティラベルが1つずつ含まれていることを確認してください。)mislabeled の単語をクリックし、ポップアップで [ラベルの削除] と [2] を選択します。ラベルを付ける必要がある単語をクリックし、ポップアップで適切なラベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-165">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="423af-167">次に、モデルを発行するために、右上にある [トレーニング] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="423af-167">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="423af-168">次に、処理が完了したら、右上の [Test] \ (テスト \) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="423af-168">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="423af-170">テキストボックスの [起動ボタンを選択してください] に「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="423af-170">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="423af-171">注: 発話のいずれかに "select" をアクションとして追加しませんでした。ただし、[検査] をクリックすると、モデルはアクションエンティティとして "select" を認識しました。</span><span class="sxs-lookup"><span data-stu-id="423af-171">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="423af-173">次に、右上にある [発行] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="423af-173">Now, click "publish" in the top right.</span></span> <span data-ttu-id="423af-174">ドロップダウンが "Production" と表示されていることを確認し、ポップアップの [発行] もクリックします。</span><span class="sxs-lookup"><span data-stu-id="423af-174">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="423af-176">発行されると、ページの上部に緑色のバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="423af-176">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="423af-177">緑色のバーをクリックして、[管理] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="423af-177">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="423af-179">左側の [アプリケーションの設定] の下にある [キーとエンドポイント] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="423af-179">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="423af-180">次に、ドロップダウンの [Publish To] を "Production" に設定します。</span><span class="sxs-lookup"><span data-stu-id="423af-180">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="423af-181">タイムゾーンを自分のものと一致するように設定し、チェックボックスをオンにしてすべての予測されたインテントスコアを含めます。</span><span class="sxs-lookup"><span data-stu-id="423af-181">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="423af-182">最後に、[リソースの割り当て] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="423af-182">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="423af-184">最初のドロップダウンから [テナント] を選択し、[サブスクリプション名] ボックスの一覧で [従量課金制] を選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-184">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="423af-185">[LUIS リソース名] の下で、手順1-5 で作成したリソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-185">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="423af-186">次に、[リソースの割り当て] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="423af-186">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="423af-188">注:次のセクションで簡単にアクセスできるように、先ほど割り当てたリソースに関連付けられているエンドポイント URL をコピーして保存してください。</span><span class="sxs-lookup"><span data-stu-id="423af-188">Note: Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="423af-189">注:テナント名には、このアプリケーション用に作成した会社またはプロファイルを入力します。</span><span class="sxs-lookup"><span data-stu-id="423af-189">Note: For the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="423af-190">次に、Unity で新しいアプリを開き、階層内の Lunarcom_Base オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-190">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="423af-191">[インスペクター] パネルの [コンポーネントの追加] をクリックし、"LunarcomIntentRecognizer" を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-191">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="423af-193">[インスペクター] パネルの [Luis Endpoint] フィールドに、手順 22. で保存したエンドポイント URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="423af-193">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="423af-195">注:[インスペクター] パネルの [LunarcomOfflineRecognizer] コンポーネントで、"disable" が "SimulateOfflineMode" に対して選択されていることを確認します。そうしないと、プログラムのテストは機能しません。</span><span class="sxs-lookup"><span data-stu-id="423af-195">Note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="423af-196">Unity エディターの [再生] ボタンをクリックし、[ロケット] ボタンをクリックして、インテント認識を開始します。</span><span class="sxs-lookup"><span data-stu-id="423af-196">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="423af-197">「Utter を選択する」という語句を選択します。</span><span class="sxs-lookup"><span data-stu-id="423af-197">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="423af-198">注:アプリは目的の関数を認識し、ロケットボタンをアクティブにしました。</span><span class="sxs-lookup"><span data-stu-id="423af-198">Note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="423af-200">結論</span><span class="sxs-lookup"><span data-stu-id="423af-200">Congratulations</span></span>

<span data-ttu-id="423af-201">このレッスンでは、AI を利用した音声コマンドを追加する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="423af-201">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="423af-202">これで、ユーザーが正確な音声コマンドを utter ない場合でも、プログラムはユーザーの意図を認識できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="423af-202">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>

