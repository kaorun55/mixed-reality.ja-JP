---
title: 音声入力
description: 音声入力の使用方法について説明します。
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality、HoloLens
ms.openlocfilehash: d61a9f9d40c76c8872ff0a1b39d65f95ae88d2b7
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835319"
---
# <a name="voice-input"></a><span data-ttu-id="335a7-104">音声入力</span><span class="sxs-lookup"><span data-stu-id="335a7-104">Voice Input</span></span>

<span data-ttu-id="335a7-105">HoloLens で音声認識を有効にするには、開発者は、プロジェクト設定 > Platform > HoloLens > の機能を使用して、Unreal エディターで "マイク" を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="335a7-105">To enable speech recognition on HoloLens, the developer needs to enable “Microphone” in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> <span data-ttu-id="335a7-106">デバイスでは、[設定 > プライバシー > 音声認識] で音声認識が有効になっていて、英語も使用されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="335a7-106">The device must also have Speech recognition enabled in Settings > Privacy > Speech and use the English language.</span></span>

![Windows 音声認識の設定](images/unreal/speech-recognition-settings.png)

<span data-ttu-id="335a7-108">サービスの品質を最大限に高めるために、オンライン音声認識を有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="335a7-108">It’s recommended to enable Online speech recognition too for the best possible quality of the service.</span></span> <span data-ttu-id="335a7-109">HoloLens での音声認識の技術的な詳細については、こちらを参照して[ください](voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="335a7-109">Technical details for speech recognition on HoloLens can be found [here](voice-input.md)</span></span>

<span data-ttu-id="335a7-110">その後、アプリケーションを初めて起動したときのマイクの有効化に関するダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="335a7-110">Then user will see a dialog about enabling the microphone when the application first starts.</span></span> <span data-ttu-id="335a7-111">ユーザーが [はい] を選択すると、アプリケーションは音声入力の取得を開始します。</span><span class="sxs-lookup"><span data-stu-id="335a7-111">If a user selects Yes, the application will begin getting voice input.</span></span>

<span data-ttu-id="335a7-112">音声入力には、特別な Windows Mixed Reality API は必要ありません。代わりに、既存の Unreal Engine 4 入力マッピング API を基に構築されています。</span><span class="sxs-lookup"><span data-stu-id="335a7-112">Speech input doesn’t require a special Windows Mixed Reality API and is instead built upon the existing Unreal Engine 4 Input mapping API.</span></span> <span data-ttu-id="335a7-113">入力 API の使用方法の詳細については、こちらを参照して[ください](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)。</span><span class="sxs-lookup"><span data-stu-id="335a7-113">Details on how to use the Input API are [here](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)</span></span>

<span data-ttu-id="335a7-114">音声マッピングが、エンジンのバインドセクションに追加されました。アクションと軸マッピングの下に入力します。</span><span class="sxs-lookup"><span data-stu-id="335a7-114">Speech Mappings have been added to the Bindings section of Engine – Input below Action and Axis Mappings.</span></span> 

![UE4 Engine 入力いいえ](images/unreal/engine-input.png)
 
<span data-ttu-id="335a7-116">ワールド "jump" の監視を追加する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="335a7-116">Here is an example of added monitoring for the world “jump”.</span></span> <span data-ttu-id="335a7-117">すべての英語の単語または短い文を使用できます。</span><span class="sxs-lookup"><span data-stu-id="335a7-117">Any English word(s) or short sentences can be used.</span></span> 

<span data-ttu-id="335a7-118">プロジェクト設定を使用して音声マッピングを追加すると、次の例に示すように、開発者は標準の Unreal ロジックを使用して入力を処理できます。</span><span class="sxs-lookup"><span data-stu-id="335a7-118">After a Speech Mapping is added via Project Settings, a developer can then use standard Unreal logic to handle the input, as in the following example:</span></span> 
 
![音声の単純なアクション](images/unreal/input-action-bp.png)
