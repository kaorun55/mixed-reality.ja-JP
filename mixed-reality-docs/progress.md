---
title: 進行状況の表示
description: プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、コントロール、ui、ux
ms.openlocfilehash: 84853a23a73bbece30c1f96b83e586642f3ab762
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523255"
---
# <a name="displaying-progress"></a>進行状況の表示

プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。 使用されているインジケーターに応じて、進行状況インジケーターが表示されているときはユーザーはアプリを操作できないことを知らせたり、待ち時間の長さを示したりできます。

![HoloLens での進行状況リングの例](images/HoloLens2_Loader.gif)<br>
*HoloLens での進行状況リングの例*

## <a name="types-of-progress"></a>プログレス コントロールの種類

何が起こっているかについてユーザー情報を提供することが重要です。 混合環境では、アプリから視覚的なフィードバックが得られない場合、ユーザーは物理環境またはオブジェクトによって簡単に気にすることができます。 データが読み込まれたりシーンが更新されたりするなど、数秒かかる状況では、視覚的なインジケーターを表示することをお勧めします。 操作が進行しているユーザーを表示するには、**進行状況バー**または**進行状況のリング**の2つのオプションがあります。

### <a name="progress-bar"></a>進行状況バー

![HoloLens での進行状況バーの例](images/640px-progressbar.jpg)

進行状況バーには、タスクの完了率が表示されます。 このメソッドは、期間が既知 (有限) の操作中に使用する必要がありますが、進行中のユーザーとアプリとの対話をブロックすることはできません。

### <a name="progress-ring"></a>進行状況リング

![HoloLens での進行状況リングの例](images/640px-progressring.jpg)

進行状況のリングは不確定な状態であるため、操作が完了するまで他のユーザー操作がブロックされたときに使用する必要があります。

### <a name="progress-with-a-custom-object"></a>カスタムオブジェクトの進行状況

![HoloLens でのカスタムメッシュの例の進行状況](images/640px-progresscustom.jpg)

独自のカスタム 2D/3D オブジェクトを使用して進行状況の制御をカスタマイズすることで、アプリの個性とブランド id に追加できます。

## <a name="best-practices"></a>ベスト プラクティス
* ユーザーが簡単にヘッドを空の領域に移動してコンテキストを失うことがあるため、 [billboarding またはタグ](billboarding-and-tag-along.md)を進行状況の表示に密に結合します。 ユーザーが何も表示できない場合、アプリがクラッシュしたように見えることがあります。 Billboarding とタグは、進行状況の prefab に組み込まれています。
* ユーザーに対して何が起こっているかに関するステータス情報を常に提供するのが適切です。 Progress prefab には、状態を提供するための Windows 標準のリングの種類の進行状況など、さまざまな視覚スタイルが用意されています。 また、進行状況のスタイルをアプリのブランドに合わせる必要がある場合は、アニメーションでカスタムメッシュを使用することもできます。

## <a name="see-also"></a>関連項目
* [Mixed Reality Toolkit での進行状況スクリプトと prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [境界ボックス](app-bar-and-bounding-box.md)
* [対話可能なオブジェクト](interactable-object.md)
* [オブジェクト コレクション](object-collection.md)
* [Billboard と Tag-along](billboarding-and-tag-along.md)
