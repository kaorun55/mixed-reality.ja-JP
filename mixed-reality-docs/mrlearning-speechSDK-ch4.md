---
title: Azure Speech Services チュートリアル-4. インテントの設定と自然言語の理解
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: e712fc2fd66b1add5b16b7dd8e6c37551aefe43a
ms.sourcegitcommit: 9005b3fdfa87ac8fdc18a594a681e25c00ac5ce1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2019
ms.locfileid: "75003211"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="5716b-105">4. インテントと自然言語の理解の設定</span><span class="sxs-lookup"><span data-stu-id="5716b-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="5716b-106">このレッスンでは、Azure Speech Service のインテント機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="5716b-106">In this lesson, you will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="5716b-107">インテント機能を使用すると、アプリケーションに AI を使用した音声コマンドが適用されます。ユーザーは、特定の音声コマンドではなく、システムによってその意図を理解できます。</span><span class="sxs-lookup"><span data-stu-id="5716b-107">The Intent feature allows you to equip our application with AI-powered voice commands, where users can say non-specific voice commands and still have their intent understood by the system.</span></span> <span data-ttu-id="5716b-108">このレッスンでは、Azure LUIS Portal を設定し、インテント/エンティティ/発話を設定し、インテントリソースを発行し、Unity アプリをインテントリソースに接続して、最初のインテント API 呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="5716b-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="5716b-109">目標</span><span class="sxs-lookup"><span data-stu-id="5716b-109">Objectives</span></span>

- <span data-ttu-id="5716b-110">アプリケーションでインテントと自然言語の理解を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5716b-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="5716b-111">Azure の LUIS ポータルを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5716b-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="5716b-112">Azure でインテント、エンティティ、および発話を設定する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="5716b-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="5716b-113">手順</span><span class="sxs-lookup"><span data-stu-id="5716b-113">Instructions</span></span>

1. <span data-ttu-id="5716b-114">コンピューターでディクテーションを有効にできるようにします。</span><span class="sxs-lookup"><span data-stu-id="5716b-114">Allow your machine to enable Dictation.</span></span> <span data-ttu-id="5716b-115">これを行うには、[Windows の設定] にアクセスし、[プライバシー]、[音声] の順に選択し、[インク & 入力] をクリックして、音声サービスをオンにして、候補を入力します。</span><span class="sxs-lookup"><span data-stu-id="5716b-115">To do this, go to Windows Settings, select "privacy," then "speech," followed by "inking & typing" and turn on speech services and typing suggestions.</span></span>

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. <span data-ttu-id="5716b-119">[Azure ポータル](https://portal.azure.com/) にログインします。</span><span class="sxs-lookup"><span data-stu-id="5716b-119">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="5716b-120">ログインしたら、[リソースの作成] をクリックし、[Language Understanding] を検索して、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5716b-120">Once you are logged in, click on Create a resource, search for "Language Understanding" and click Enter.</span></span>

    ![mrlearning-speech-ch4-1-step2](images/mrlearning-speech-ch4-1-step2.png)

3. <span data-ttu-id="5716b-122">このサービスのインスタンスを作成するには、 **[作成]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-122">Click the **Create** button to create an instance of this service.</span></span>

    ![mrlearning-speech-ch4-1-step3a](images/mrlearning-speech-ch4-1-step3a.png)

    <span data-ttu-id="5716b-124">リソースに**名前**を付けます。たとえば、「 *Speech-SDK-Learning-Module*」と指定します。</span><span class="sxs-lookup"><span data-stu-id="5716b-124">Give your resource a **Name**, for example, *Speech-SDK-Learning-Module*.</span></span> <span data-ttu-id="5716b-125">**サブスクリプション**については、試用版アカウントをお持ちの場合は、*従量課金制*または*無料証跡*を選択します。</span><span class="sxs-lookup"><span data-stu-id="5716b-125">For **Subscription**, select *Pay As You Go* or *Free Trail* if you have a trial account.</span></span> <span data-ttu-id="5716b-126">次に、 **[新規作成]** リンクをクリックして新しい**リソースグループ**を作成し、たとえば「 *HoloLens-2-チュートリアル-リソースグループ*」という名前を入力して、 **[OK]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-126">Next, create a new **Resource Group** by clicking the **Create new** link, enter a name, for example, *HoloLens-2-Tutorials-Resource-Group*, and click the **OK** button.</span></span>

    ![mrlearning-speech-ch4-1-step3b](images/mrlearning-speech-ch4-1-step3b.png)

4. <span data-ttu-id="5716b-128">**作成場所**と**実行時の場所**を選択します。</span><span class="sxs-lookup"><span data-stu-id="5716b-128">Select your **Authoring location** and **Runtime location**.</span></span> <span data-ttu-id="5716b-129">このチュートリアルでは、[*米国西部*] を使用します。次に、 **[オーサリング価格レベル]** と **[ランタイム価格レベル]** に [ *F0] (1 秒あたり5回、1か月あたり10,000 回)* を選択します。</span><span class="sxs-lookup"><span data-stu-id="5716b-129">For the purpose of this tutorial, use *(US) West US*, then choose *F0 (5 Calls per second, 10K Calls per month)* for the **Authoring pricing tier** and **Runtime pricing tier**.</span></span> <span data-ttu-id="5716b-130">最後に、 **[作成]** ボタンをクリックして、新しいリソースグループだけでなく、リソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="5716b-130">Finally, click the **Create** button to create the resource, as well as the new resource group.</span></span>

    ![mrlearning-speech-ch4-1-step4](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    ><span data-ttu-id="5716b-132">[作成] ボタンをクリックした後、サービスが作成されるまで待機する必要があります。これには数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5716b-132">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

5. <span data-ttu-id="5716b-133">リソースの作成プロセスが完了すると、**デプロイが完了**したことを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5716b-133">Once the resource creation process is complete, you will see the message **Your deployment is complete**.</span></span>

    ![mrlearning-speech-ch4-1-step5](images/mrlearning-speech-ch4-1-step5.png)

6. <span data-ttu-id="5716b-135">同じユーザーアカウントを使用して、 [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/)ポータルにサインインし、お住まいの国を選択して、使用条件に同意します。</span><span class="sxs-lookup"><span data-stu-id="5716b-135">Using the same user account, sign in to the [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/) portal, select your country, and agree to the terms of use.</span></span>

    >[!NOTE]
    ><span data-ttu-id="5716b-136">Language Understanding ポータルに達したら、Azure portal と同じ資格情報を使用してログインする必要がある場合があります (まだログインしていない場合)。</span><span class="sxs-lookup"><span data-stu-id="5716b-136">Upon reaching the Language Understanding portal, you may need to log in, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="5716b-137">LUIS を初めて使用する場合は、[ようこそ] ページの一番下までスクロールして [Create LUIS] \ (アプリの作成 \) ボタンをクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5716b-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the Welcome page to find and click the "Create LUIS" app button.</span></span>

7. <span data-ttu-id="5716b-138">ログインしたら、[マイアプリ] をクリックします (現在このセクションにない場合)。</span><span class="sxs-lookup"><span data-stu-id="5716b-138">Once logged in, click My Apps (if you are not currently in that section).</span></span> <span data-ttu-id="5716b-139">[新しいアプリの作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-139">You can then click on Create new app.</span></span> <span data-ttu-id="5716b-140">新しいアプリに "Speech SDK Learning Module" という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5716b-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="5716b-141">"Speech SDK Learning Module" を [説明] フィールドにも追加します。</span><span class="sxs-lookup"><span data-stu-id="5716b-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="5716b-142">[完了] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-142">Then click "done."</span></span>

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    ><span data-ttu-id="5716b-145">アプリが英語とは異なる言語を認識する場合は、"Culture" を適切な言語に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5716b-145">If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

8. <span data-ttu-id="5716b-146">右上にある [ビルド] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-146">Click “Build” located in the top right.</span></span>

9. <span data-ttu-id="5716b-147">左側の [アプリ資産] で、[インテント] を選択し、[新しいインテントの作成] をクリックして、"PressButton" という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5716b-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span>

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    ><span data-ttu-id="5716b-149">このチュートリアルで使用するインテントとエンティティの名前は、Lunarcom アプリが名前で参照するため、使用することが重要です。</span><span class="sxs-lookup"><span data-stu-id="5716b-149">It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>

    >[!NOTE]
    ><span data-ttu-id="5716b-150">これで、"PressButton" と "None" の2つのインテントが作成されました。</span><span class="sxs-lookup"><span data-stu-id="5716b-150">You should now have 2 Intents - “PressButton” and “None."</span></span>

10. <span data-ttu-id="5716b-151">左側の [アプリ資産] で、[エンティティ] を選択し、[新しいエンティティの作成] をクリックして、「アクション」という名前を付け、エンティティ型を "Simple" として保持します。</span><span class="sxs-lookup"><span data-stu-id="5716b-151">Under App Assets on the left, select “Entities”, click “Create New Entity”, name it “Action” and keep the Entity Type as “Simple.”</span></span>

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. <span data-ttu-id="5716b-153">[新しいエンティティの作成] をもう一度クリックし、"Target" という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5716b-153">Click “Create New Entity” again and name it “Target”.</span></span> <span data-ttu-id="5716b-154">エンティティ型も "Simple" として保持します。</span><span class="sxs-lookup"><span data-stu-id="5716b-154">Keep the Entity Type as “Simple”, as well.</span></span>

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. <span data-ttu-id="5716b-156">左側の [アプリ資産] で、[インテント] を選択し、手順 10. で作成した "PressButton" インテントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-156">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. <span data-ttu-id="5716b-158">右側の [表示オプション] ドロップダウンをクリックし、[エンティティ値の表示] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5716b-158">Click the "View options" dropdown on the right and select "show entity values."</span></span>

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    <span data-ttu-id="5716b-160">[例を入力してください...] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-160">Click the “Enter an example…”</span></span> <span data-ttu-id="5716b-161">ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="5716b-161">textbox.</span></span> <span data-ttu-id="5716b-162">次に、次の発話を入力します。</span><span class="sxs-lookup"><span data-stu-id="5716b-162">Then, enter the following utterances:</span></span>

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. <span data-ttu-id="5716b-164">右側の [表示オプション] ドロップダウンをクリックし、[エンティティ名の表示] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5716b-164">Click the "View options" dropdown on the right and select "Show entity names."</span></span>

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. <span data-ttu-id="5716b-166">10の各発話に、次のエンティティラベルが1つずつ含まれていることを確認してください。)mislabeled の単語をクリックし、ポップアップで [ラベルの削除] と [2] を選択します。ラベルを付ける必要がある単語をクリックし、ポップアップで適切なラベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="5716b-166">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. <span data-ttu-id="5716b-168">次に、モデルを発行するために、右上にある [トレーニング] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-168">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="5716b-169">次に、処理が完了したら、右上の [Test] \ (テスト \) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-169">Then, once it has finished processing, click "Test" in the top right.</span></span>

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. <span data-ttu-id="5716b-171">テキストボックスの [起動ボタンを選択してください] に「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="5716b-171">Enter in “select the launch button” in  the textbox.</span></span>

    >[!NOTE]
    ><span data-ttu-id="5716b-172">発話のいずれかに "select" をアクションとして追加しませんでしたが、[検査] をクリックすると、モデルはアクションエンティティとして "select" を認識しました。</span><span class="sxs-lookup"><span data-stu-id="5716b-172">We did not add “select” as an action in any of our Utterances, but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. <span data-ttu-id="5716b-174">右上にある [発行] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-174">Click "publish" in the top right.</span></span> <span data-ttu-id="5716b-175">ドロップダウンが "Production" と表示されていることを確認し、ポップアップの [発行] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-175">Ensure the dropdown says “Production” and click "publish" on the popup, as well.</span></span>

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. <span data-ttu-id="5716b-177">発行されると、ページの上部に緑色のバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5716b-177">Once published, a green bar should appear at the top of the page.</span></span> <span data-ttu-id="5716b-178">緑色のバーをクリックすると、[管理] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5716b-178">Click the green bar to view the "Manage" page.</span></span>

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. <span data-ttu-id="5716b-180">左側の [アプリケーションの設定] の下にある [キーとエンドポイント] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-180">Click "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="5716b-181">次に、ドロップダウンの [Publish To] を "Production" に設定します。</span><span class="sxs-lookup"><span data-stu-id="5716b-181">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="5716b-182">タイムゾーンを自分のものと一致するように設定し、チェックボックスをオンにしてすべての予測されたインテントスコアを含めます。</span><span class="sxs-lookup"><span data-stu-id="5716b-182">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="5716b-183">最後に、[リソースの割り当て] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-183">Lastly, click "Assign resource."</span></span>

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. <span data-ttu-id="5716b-185">最初のドロップダウンから [テナント] を選択し、[サブスクリプション名] ボックスの一覧で [従量課金制] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5716b-185">Select tenant from the first dropdown and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="5716b-186">[LUIS リソース名] の下で、手順1-5 で作成したリソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="5716b-186">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="5716b-187">次に、[リソースの割り当て] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5716b-187">Then, click on "Assign resource."</span></span>

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    ><span data-ttu-id="5716b-189">次のセクションで簡単にアクセスできるように、先ほど割り当てたリソースに関連付けられているエンドポイント URL をコピーして保存してください。</span><span class="sxs-lookup"><span data-stu-id="5716b-189">Ensure to copy and save the Endpoint URL associated with the resource we just assigned so it is easily accessible for the next section.</span></span>

    >[!NOTE]
    ><span data-ttu-id="5716b-190">テナント名には、このアプリケーション用に作成した会社またはプロファイルを入力します。</span><span class="sxs-lookup"><span data-stu-id="5716b-190">For the Tenant name, put your corporation or profile that you created for this application.</span></span>

22. <span data-ttu-id="5716b-191">次に、Unity で新しいアプリを開き、階層内の Lunarcom_Base オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="5716b-191">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="5716b-192">[インスペクター] パネルの [コンポーネントの追加] をクリックし、"LunarcomIntentRecognizer" を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="5716b-192">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. <span data-ttu-id="5716b-194">[インスペクター] パネルの [Luis Endpoint] フィールドに、手順 22. で保存したエンドポイント URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="5716b-194">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    ><span data-ttu-id="5716b-196">[インスペクター] パネルの [LunarcomOfflineRecognizer] コンポーネントで、"disable" が "SimulateOfflineMode" に対して選択されていることを確認します。そうしないと、プログラムのテストは機能しません。</span><span class="sxs-lookup"><span data-stu-id="5716b-196">In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span>

24. <span data-ttu-id="5716b-197">Unity エディターの [再生] ボタンをクリックし、[ロケット] ボタンをクリックして、インテント認識を開始します。</span><span class="sxs-lookup"><span data-stu-id="5716b-197">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="5716b-198">「Utter を選択する」という語句を選択します。</span><span class="sxs-lookup"><span data-stu-id="5716b-198">Utter the phrase “select the launch rocket button.”</span></span>

    >[!NOTE]
    ><span data-ttu-id="5716b-199">アプリは目的の関数を認識し、ロケットボタンをアクティブにしました。</span><span class="sxs-lookup"><span data-stu-id="5716b-199">The app recognized the desired function and activated the rocket button.</span></span>
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="5716b-201">結論</span><span class="sxs-lookup"><span data-stu-id="5716b-201">Congratulations</span></span>

<span data-ttu-id="5716b-202">このレッスンでは、AI を使用した音声コマンドを追加する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="5716b-202">In this lesson, you learned how to add AI-powered speech commands.</span></span> <span data-ttu-id="5716b-203">これで、ユーザーが正確な音声コマンドを utter ない場合でも、プログラムはユーザーの意図を認識できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="5716b-203">Now your program can recognize users' intent, even if they do not utter precise voice commands!</span></span>
