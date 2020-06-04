---
title: 音声入力
description: HoloLens 2 および Unreal engine での音声入力の設定と使用に関するチュートリアル
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality、Unreal、Unreal Engine 4、UE4、HoloLens 2、音声、音声入力、音声認識、Mixed Reality、開発、機能、ドキュメント、ガイド、ホログラム、ゲーム開発
ms.openlocfilehash: c5de0cd912674ccd681fd398fb6fe5fd345ab6f2
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330634"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="08ff8-104">Unreal での音声入力</span><span class="sxs-lookup"><span data-stu-id="08ff8-104">Voice Input in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="08ff8-105">概要</span><span class="sxs-lookup"><span data-stu-id="08ff8-105">Overview</span></span>
<span data-ttu-id="08ff8-106">音声入力を使用すると、ハンドジェスチャを使用しなくても、また HoloLens (第1世代) と HoloLens 2 でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="08ff8-106">Voice input allows you to interact with a hologram without having to use hand gestures and is supported on HoloLens (1st Gen) and HoloLens 2.</span></span> <span data-ttu-id="08ff8-107">これは、他のすべてのユニバーサル Windows アプリで音声をサポートするのと同じエンジンによって機能し、混合現実の対話方法に自然な感覚を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="08ff8-107">It's powered by the same engine that supports speech in all other Universal Windows Apps and can add a natural feeling to the way you interact in mixed reality.</span></span> 

<span data-ttu-id="08ff8-108">サポートされている音声機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="08ff8-108">Supported voice features include:</span></span>
- <span data-ttu-id="08ff8-109">[Select コマンド](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span><span class="sxs-lookup"><span data-stu-id="08ff8-109">The [Select command](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span></span>
- [<span data-ttu-id="08ff8-110">Cortana さん、こんにちは</span><span class="sxs-lookup"><span data-stu-id="08ff8-110">Hey, Cortana</span></span>](https://docs.microsoft.com/windows/mixed-reality/voice-input#hey-cortana)
- <span data-ttu-id="08ff8-111">「ボタンとラベルの相互作用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08ff8-111">"See it, say it" for button and label interaction</span></span>
- <span data-ttu-id="08ff8-112">ディクテーション</span><span class="sxs-lookup"><span data-stu-id="08ff8-112">Dictation</span></span>

<span data-ttu-id="08ff8-113">詳細については、主な[音声入力](voice-input.md)のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="08ff8-113">For more information, check out the main [Voice Input](voice-input.md) documentation.</span></span>

## <a name="enabling-speech-recognition"></a><span data-ttu-id="08ff8-114">音声認識を有効にする</span><span class="sxs-lookup"><span data-stu-id="08ff8-114">Enabling Speech Recognition</span></span>

<span data-ttu-id="08ff8-115">HoloLens で音声認識を有効にするには:</span><span class="sxs-lookup"><span data-stu-id="08ff8-115">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="08ff8-116">[プロジェクトの設定] を選択して **> プラットフォーム > HoloLens > 機能**を選択し、**マイク**を有効にします。</span><span class="sxs-lookup"><span data-stu-id="08ff8-116">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="08ff8-117">[設定] で音声認識を有効にしました。 **> プライバシー > 音声**で、[**英語**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="08ff8-117">Enabled speech recogniztion in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="08ff8-118">音声認識は常に、**設定**アプリで構成された Windows 表示言語で機能します。</span><span class="sxs-lookup"><span data-stu-id="08ff8-118">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="08ff8-119">また、サービス品質を最大限に高めるために、**オンライン音声認識**を有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="08ff8-119">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Windows 音声認識の設定](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="08ff8-121">アプリケーションが最初にマイクを有効にするかどうかを確認すると、ダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="08ff8-121">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="08ff8-122">**[はい]** を選択すると、アプリで音声入力が開始されます。</span><span class="sxs-lookup"><span data-stu-id="08ff8-122">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="08ff8-123">音声入力には、特別な Windows Mixed Reality Api は必要ありません。これは、既存の Unreal Engine 4[入力](https://docs.unrealengine.com/Gameplay/Input/index.html)マッピング API を基に構築されています。</span><span class="sxs-lookup"><span data-stu-id="08ff8-123">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="08ff8-124">音声マッピングの追加</span><span class="sxs-lookup"><span data-stu-id="08ff8-124">Adding Speech Mappings</span></span>
<span data-ttu-id="08ff8-125">音声入力を使用する場合は、音声をアクションに接続することが重要な手順です。</span><span class="sxs-lookup"><span data-stu-id="08ff8-125">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="08ff8-126">これらのマッピングは、ユーザーが話す可能性のある音声キーワードをアプリで監視し、リンクされたアクションを起動します。</span><span class="sxs-lookup"><span data-stu-id="08ff8-126">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="08ff8-127">音声マッピングは、次の方法で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="08ff8-127">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="08ff8-128">[**プロジェクト設定の編集 >**] を選択し、[**エンジン**] セクションまでスクロールして [**入力**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08ff8-128">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="08ff8-129">ジャンプコマンドの新しい音声マッピングを追加するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="08ff8-129">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="08ff8-130">[ **+** **配列要素**] の横にあるアイコンをクリックし、次の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="08ff8-130">Click the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="08ff8-131">**アクション名**の**jumpWord**</span><span class="sxs-lookup"><span data-stu-id="08ff8-131">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="08ff8-132">**Speech キーワード**の**ジャンプ**</span><span class="sxs-lookup"><span data-stu-id="08ff8-132">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="08ff8-133">すべての英語の単語または短い文をキーワードとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="08ff8-133">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![UE4 Engine 入力いいえ](images/unreal/engine-input.png)

<span data-ttu-id="08ff8-135">音声マッピングは、アクションや軸のマッピングなどの入力コンポーネントとして、またはイベントグラフのブループリントノードとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="08ff8-135">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="08ff8-136">たとえば、ジャンプコマンドをリンクして、単語が話されるタイミングに応じて2つの異なるログを出力することができます。</span><span class="sxs-lookup"><span data-stu-id="08ff8-136">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="08ff8-137">ブループリントをダブルクリックして、**イベントグラフ**で開きます。</span><span class="sxs-lookup"><span data-stu-id="08ff8-137">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="08ff8-138">**右クリック**して音声マッピングの**アクション名**(この場合は**jumpWord**) を検索し、 **enter キー**を押します。</span><span class="sxs-lookup"><span data-stu-id="08ff8-138">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter**.</span></span> <span data-ttu-id="08ff8-139">これにより、グラフに**入力アクション**ノードが追加されます。</span><span class="sxs-lookup"><span data-stu-id="08ff8-139">This adds an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="08ff8-140">次の図に示すように、**押さ**れた pin をドラッグアンドドロップして文字列ノードを**印刷**します。</span><span class="sxs-lookup"><span data-stu-id="08ff8-140">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="08ff8-141">**解放**された pin は空のままにすることができ、音声マッピングの場合は何も実行されません。</span><span class="sxs-lookup"><span data-stu-id="08ff8-141">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![音声の単純なアクション](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="08ff8-143">アプリを再生します。 word の**ジャンプ**を言い、コンソールでログを出力します。</span><span class="sxs-lookup"><span data-stu-id="08ff8-143">Play the app, say the word **jump** and watch the console print out the logs!</span></span>

<span data-ttu-id="08ff8-144">これで、HoloLens アプリへの音声入力の追加を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08ff8-144">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="08ff8-145">音声と対話機能の詳細については、以下のリンクを参照してください。ユーザー向けに作成しているエクスペリエンスについて考えてください。</span><span class="sxs-lookup"><span data-stu-id="08ff8-145">You can find more information on speech and interactivity can be found at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="see-also"></a><span data-ttu-id="08ff8-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="08ff8-146">See also</span></span>
* [<span data-ttu-id="08ff8-147">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="08ff8-147">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="08ff8-148">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="08ff8-148">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="08ff8-149">MR 入力 212:音声</span><span class="sxs-lookup"><span data-stu-id="08ff8-149">MR Input 212: Voice</span></span>](holograms-212.md)
