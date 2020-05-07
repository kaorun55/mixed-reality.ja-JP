---
title: Unreal の入力を見つめます
description: Unreal での、宝石入力の使用方法について説明します。
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、HoloLens、アイ tracking
ms.openlocfilehash: 7387bb3f25cdbdfac32f508c173fbd098f844e84
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835627"
---
# <a name="gaze-input"></a><span data-ttu-id="a1347-104">見つめ入力</span><span class="sxs-lookup"><span data-stu-id="a1347-104">Gaze Input</span></span>

<span data-ttu-id="a1347-105">Windows Mixed Reality プラグインには、宝石入力用の特別な機能は用意されていません。</span><span class="sxs-lookup"><span data-stu-id="a1347-105">The Windows Mixed Reality plugin doesn’t provide any special functions for the gaze input.</span></span> <span data-ttu-id="a1347-106">すべてが標準の Unreal API で動作します。</span><span class="sxs-lookup"><span data-stu-id="a1347-106">Everything works though the standard Unreal API.</span></span>

[<span data-ttu-id="a1347-107">ヘッドを見つめた API</span><span class="sxs-lookup"><span data-stu-id="a1347-107">Head gaze API</span></span>](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a><span data-ttu-id="a1347-108">視線追跡</span><span class="sxs-lookup"><span data-stu-id="a1347-108">Eye tracking</span></span>

<span data-ttu-id="a1347-109">視線追跡 API を使用するには、開発者が HoloLens プロジェクトの設定で "宝石入力" 機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1347-109">To use the eye tracking API, developers should enable the “Gaze Input” capability in their HoloLens project settings.</span></span> <span data-ttu-id="a1347-110">アプリケーションが起動すると、ユーザーには次の同意プロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a1347-110">When the application starts, user will see the following consent prompt</span></span>

![アイ入力のアクセス許可](images/unreal/eye-input-permissions.png)
 
<span data-ttu-id="a1347-112">ユーザーがアクセス許可を付与すると、アプリケーションは目を見つめた入力を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a1347-112">If the user gives their permission, the application will get eye gaze input.</span></span> 

<span data-ttu-id="a1347-113">Unreal の監視 API については、こちらを参照して[ください](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)。</span><span class="sxs-lookup"><span data-stu-id="a1347-113">Unreal’s eye tracking API is documented is [here](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)</span></span>

<span data-ttu-id="a1347-114">視線追跡の技術的な詳細については、こちらを参照して[ください](eye-tracking.md)。</span><span class="sxs-lookup"><span data-stu-id="a1347-114">The technical details of eye tracking are [here](eye-tracking.md)</span></span>

<span data-ttu-id="a1347-115">特に、非 Real の場合、HoloLens の追跡では、両方の目に1つの宝石があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a1347-115">Note that specifically for Unreal, HoloLens eye tracking has a single gaze ray for both eyes.</span></span> <span data-ttu-id="a1347-116">HoloLens は、ステレオスコピック目の追跡を提供しません。</span><span class="sxs-lookup"><span data-stu-id="a1347-116">HoloLens doesn’t provide stereoscopic eye tracking.</span></span>
