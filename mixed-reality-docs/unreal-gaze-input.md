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
# <a name="gaze-input"></a>見つめ入力

Windows Mixed Reality プラグインには、宝石入力用の特別な機能は用意されていません。 すべてが標準の Unreal API で動作します。

[ヘッドを見つめた API](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a>視線追跡

視線追跡 API を使用するには、開発者が HoloLens プロジェクトの設定で "宝石入力" 機能を有効にする必要があります。 アプリケーションが起動すると、ユーザーには次の同意プロンプトが表示されます。

![アイ入力のアクセス許可](images/unreal/eye-input-permissions.png)
 
ユーザーがアクセス許可を付与すると、アプリケーションは目を見つめた入力を受け取ります。 

Unreal の監視 API については、こちらを参照して[ください](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)。

視線追跡の技術的な詳細については、こちらを参照して[ください](eye-tracking.md)。

特に、非 Real の場合、HoloLens の追跡では、両方の目に1つの宝石があることに注意してください。 HoloLens は、ステレオスコピック目の追跡を提供しません。
