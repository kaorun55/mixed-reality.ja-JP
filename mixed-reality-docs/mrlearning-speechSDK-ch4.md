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
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="d7775-105">4。インテントの設定と自然言語の理解</span><span class="sxs-lookup"><span data-stu-id="d7775-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="d7775-106">このレッスンでは、Azure Speech Service のインテント機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7775-106">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="d7775-107">インテント機能を使用すると、アプリケーションに AI を使用した音声コマンドを提供できるようになります。この場合、ユーザーは特に特定できない音声コマンドを読み上げ、システムがその意図を理解することができます。</span><span class="sxs-lookup"><span data-stu-id="d7775-107">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="d7775-108">このレッスンでは、Azure LUIS Portal を設定し、インテント/エンティティ/発話を設定し、インテントリソースを発行し、Unity アプリをインテントリソースに接続して、最初のインテント API 呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="d7775-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="d7775-109">目的</span><span class="sxs-lookup"><span data-stu-id="d7775-109">Objectives</span></span>

- <span data-ttu-id="d7775-110">アプリケーションでインテントと自然言語の理解を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7775-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="d7775-111">Azure の LUIS ポータルを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7775-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="d7775-112">Azure でインテント、エンティティ、および発話を設定する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="d7775-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="d7775-113">手順</span><span class="sxs-lookup"><span data-stu-id="d7775-113">Instructions</span></span>
1. <span data-ttu-id="d7775-114">コンピューターでディクテーションを有効にするには、この操作を行うには、[Windows の設定] にアクセスし、[プライバシー]、[& 音声] の順に選択して、音声サービスをオンにして、候補を入力します。</span><span class="sxs-lookup"><span data-stu-id="d7775-114">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. <span data-ttu-id="d7775-118">[Azure ポータル](https://portal.azure.com/) にログインします。</span><span class="sxs-lookup"><span data-stu-id="d7775-118">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="d7775-119">ログインしたら、[リソースの作成] をクリックし、[Language Understanding] を検索して、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d7775-119">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="d7775-121">このサービスのインスタンスを作成するには、[作成] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-121">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="d7775-122">プロジェクトに "Speech_SDK_Learning_Module" という名前を付け、[従量課金制] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-122">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="d7775-125">リージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-125">Select your Region.</span></span>  <span data-ttu-id="d7775-126">このチュートリアルでは、[米国西部] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-126">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="d7775-127">次に、価格レベルとして "F0" を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-127">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="d7775-128">次に、(左下隅にある) [作成] をクリックして、リソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="d7775-128">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

>  <span data-ttu-id="d7775-129">注: [作成] をクリックすると、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="d7775-129">Note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="d7775-130">リソースが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7775-130">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="d7775-131">この通知をクリックし、[リソースへのアクセス] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-131">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="d7775-132">"LUIS API" サービスの [クイックスタート] ページで、最初の手順に移動し、[キー] をクリックして、[キー] をクリックします (次の図に示されている青いハイパーリンク "キー" をクリックして、これを実現することもできます)。</span><span class="sxs-lookup"><span data-stu-id="d7775-132">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="d7775-133">これにより、サービス "キー" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7775-133">This will reveal your service, "Keys."</span></span> <span data-ttu-id="d7775-134">アプリで後で使用できるように、いずれかのキーのコピーを保存します。</span><span class="sxs-lookup"><span data-stu-id="d7775-134">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="d7775-136">セクション2b の下にある [クイックスタート] ページに戻り、[Language Understanding ポータル] (上の図を参照) をクリックして、LUIS アプリケーション内で新しいサービスの作成に使用する web ページにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="d7775-136">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="d7775-137">注:"Language Understanding ポータル" に到達した場合は、Azure portal と同じ資格情報を使用してログインする必要があります (まだログインしていない場合)。</span><span class="sxs-lookup"><span data-stu-id="d7775-137">Note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="d7775-138">LUIS を初めて使用する場合は、[ようこそ] ページの一番下までスクロールして、[Create LUIS] \ (アプリの作成 \) ボタンを見つけてクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7775-138">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="d7775-139">ログインしたら、[マイアプリ] をクリックします (現在このセクションにない場合)。</span><span class="sxs-lookup"><span data-stu-id="d7775-139">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="d7775-140">[新しいアプリの作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7775-140">You can then click on Create new app.</span></span> <span data-ttu-id="d7775-141">新しいアプリに "Speech SDK Learning Module" という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d7775-141">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="d7775-142">"Speech SDK Learning Module" を [説明] フィールドにも追加します。</span><span class="sxs-lookup"><span data-stu-id="d7775-142">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="d7775-143">[完了] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7775-143">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="d7775-146">付箋アプリが英語とは異なる言語を認識する場合は、"Culture" を適切な言語に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7775-146">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="d7775-147">右上にある [ビルド] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7775-147">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="d7775-148">左側の [アプリ資産] で、[インテント] を選択し、[新しいインテントの作成] をクリックして、"PressButton" という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d7775-148">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="d7775-150">注:このチュートリアルで使用するインテントとエンティティの名前は、Lunarcom アプリが名前で参照するため、使用することが重要です。</span><span class="sxs-lookup"><span data-stu-id="d7775-150">Note: It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span> 
>
> <span data-ttu-id="d7775-151">注: "PressButton" と "None" の2つのインテントがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d7775-151">Note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="d7775-152">左側の [アプリ資産] で、[エンティティ] を選択し、[新しいエンティティの作成] をクリックして、"Action" という名前を付け、エンティティ型を "Simple" にしておきます。</span><span class="sxs-lookup"><span data-stu-id="d7775-152">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="d7775-154">[新しいエンティティの作成] をもう一度クリックし、"Target" という名前を付けて、エンティティ型を "Simple" として保持します。</span><span class="sxs-lookup"><span data-stu-id="d7775-154">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="d7775-156">左側の [アプリ資産] で、[インテント] を選択し、手順 10. で作成した "PressButton" インテントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7775-156">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="d7775-158">右側の [表示オプション] ドロップダウンをクリックし、[エンティティ値の表示] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-158">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="d7775-160">[例を入力してください...] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7775-160">Click on the “Enter an example…”</span></span> <span data-ttu-id="d7775-161">wl.</span><span class="sxs-lookup"><span data-stu-id="d7775-161">textbox.</span></span> <span data-ttu-id="d7775-162">次に、次の発話を入力します。</span><span class="sxs-lookup"><span data-stu-id="d7775-162">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="d7775-164">右側の [表示オプション] ドロップダウンをクリックし、[エンティティ名の表示] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-164">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="d7775-166">10の各発話に、次のエンティティラベルが1つずつ含まれていることを確認してください。)mislabeled の単語をクリックし、ポップアップで [ラベルの削除] と [2] を選択します。ラベルを付ける必要がある単語をクリックし、ポップアップで適切なラベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-166">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="d7775-168">次に、モデルを発行するために、右上にある [トレーニング] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7775-168">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="d7775-169">次に、処理が完了したら、右上の [Test] \ (テスト \) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7775-169">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="d7775-171">テキストボックスの [起動ボタンを選択してください] に「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d7775-171">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="d7775-172">注: 発話のいずれかに "select" をアクションとして追加しませんでした。ただし、[検査] をクリックすると、モデルはアクションエンティティとして "select" を認識しました。</span><span class="sxs-lookup"><span data-stu-id="d7775-172">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="d7775-174">次に、右上にある [発行] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7775-174">Now, click "publish" in the top right.</span></span> <span data-ttu-id="d7775-175">ドロップダウンが "Production" と表示されていることを確認し、ポップアップの [発行] もクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7775-175">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="d7775-177">発行されると、ページの上部に緑色のバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7775-177">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="d7775-178">緑色のバーをクリックして、[管理] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="d7775-178">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="d7775-180">左側の [アプリケーションの設定] の下にある [キーとエンドポイント] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7775-180">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="d7775-181">次に、ドロップダウンの [Publish To] を "Production" に設定します。</span><span class="sxs-lookup"><span data-stu-id="d7775-181">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="d7775-182">タイムゾーンを自分のものと一致するように設定し、チェックボックスをオンにしてすべての予測されたインテントスコアを含めます。</span><span class="sxs-lookup"><span data-stu-id="d7775-182">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="d7775-183">最後に、[リソースの割り当て] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7775-183">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="d7775-185">最初のドロップダウンから [テナント] を選択し、[サブスクリプション名] ボックスの一覧で [従量課金制] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-185">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="d7775-186">[LUIS リソース名] の下で、手順1-5 で作成したリソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-186">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="d7775-187">次に、[リソースの割り当て] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7775-187">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="d7775-189">注:次のセクションで簡単にアクセスできるように、先ほど割り当てたリソースに関連付けられているエンドポイント URL をコピーして保存してください。</span><span class="sxs-lookup"><span data-stu-id="d7775-189">Note: Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="d7775-190">注:テナント名には、このアプリケーション用に作成した会社またはプロファイルを入力します。</span><span class="sxs-lookup"><span data-stu-id="d7775-190">Note: For the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="d7775-191">次に、Unity で新しいアプリを開き、階層内の Lunarcom_Base オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-191">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="d7775-192">[インスペクター] パネルの [コンポーネントの追加] をクリックし、"LunarcomIntentRecognizer" を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-192">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="d7775-194">[インスペクター] パネルの [Luis Endpoint] フィールドに、手順 22. で保存したエンドポイント URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="d7775-194">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="d7775-196">注:[インスペクター] パネルの [LunarcomOfflineRecognizer] コンポーネントで、"disable" が "SimulateOfflineMode" に対して選択されていることを確認します。そうしないと、プログラムのテストは機能しません。</span><span class="sxs-lookup"><span data-stu-id="d7775-196">Note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="d7775-197">Unity エディターの [再生] ボタンをクリックし、[ロケット] ボタンをクリックして、インテント認識を開始します。</span><span class="sxs-lookup"><span data-stu-id="d7775-197">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="d7775-198">「Utter を選択する」という語句を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7775-198">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="d7775-199">注:アプリは目的の関数を認識し、ロケットボタンをアクティブにしました。</span><span class="sxs-lookup"><span data-stu-id="d7775-199">Note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="d7775-201">結論</span><span class="sxs-lookup"><span data-stu-id="d7775-201">Congratulations</span></span>

<span data-ttu-id="d7775-202">このレッスンでは、AI を利用した音声コマンドを追加する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="d7775-202">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="d7775-203">これで、ユーザーが正確な音声コマンドを utter ない場合でも、プログラムはユーザーの意図を認識できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d7775-203">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>

