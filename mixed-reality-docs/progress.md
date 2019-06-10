---
title: 進行状況の表示
description: プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、コントロール、ui、ux
ms.openlocfilehash: d62d86c690233f351b6c156c66eba33cb2687ea6
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813731"
---
# <a name="displaying-progress"></a>進行状況の表示

プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。 使用されているインジケーターに応じて、進行状況インジケーターが表示されているときはユーザーはアプリを操作できないことを知らせたり、待ち時間の長さを示したりできます。

![HoloLens の進行状況リングの例](images/HoloLens2_Loader.gif)<br>
*HoloLens の進行状況リングの例*

## <a name="types-of-progress"></a>プログレス コントロールの種類

ユーザーが何が起こっているかに関する情報を提供する重要です。 複合現実でユーザーことができますが簡単に気を取られる物理環境またはオブジェクトの場合、アプリはありませんで適切な視覚的なフィードバック。 数秒かかる場合、データの読み込み時にこのようなまたはシーンを更新、視覚インジケータを表示することをお勧めします。 操作が進行中 – ですが、ユーザーを表示する 2 つのオプションがあります、**進行状況バー**または**進行状況リング**します。

### <a name="progress-bar"></a>進行状況バー

![HoloLens で進行状況バーの例](images/640px-progressbar.jpg)

進行状況バーは、タスクの完了率を示しています。 ある期間がわかっている (不確定)、操作中にために使用する必要がありますが、進行状況は、アプリでのユーザーの操作をブロックしないでください。

### <a name="progress-ring"></a>進行状況リング

![HoloLens の進行状況リングの例](images/640px-progressring.jpg)

進行状況リングは、中間の状態がのみと、操作が完了するまで、さらに、ユーザーの操作がブロックされたときに使用する必要があります。

### <a name="progress-with-a-custom-object"></a>カスタム オブジェクトでの進行状況

![HoloLens でカスタムのメッシュの例での進行状況](images/640px-progresscustom.jpg)

カスタム 2d/3d オブジェクトで進行状況コントロールをカスタマイズすることで、アプリのパーソナリティとブランド id に追加できます。

## <a name="best-practices"></a>ベスト プラクティス
* 密に結合[ビルボード処理または tag-along](billboarding-and-tag-along.md)を簡単にユーザーは自分の頭を空の領域に移動し、コンテキストが失われるため、進行状況の表示にします。 アプリがクラッシュした場合は、ユーザーが何も表示できないように見える場合があります。 Billboarding と tag-along は、進行状況のプレハブに組み込まれています。
* ユーザーに何が起こっているかに関する状態情報を提供することをお勧めします。 進行状況のプレハブは、状態を提供するための Windows リング型の標準的な進行状況を含む、さまざまな視覚スタイルを提供します。 場合は、アプリのブランドに合わせるために、進行状況のスタイルは、アニメーションがカスタム メッシュを使用することもできます。

## <a name="see-also"></a>関連項目
* [進行状況のスクリプトや Mixed Reality Toolkit のプレハブ](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [境界ボックス](app-bar-and-bounding-box.md)
* [対話可能なオブジェクト](interactable-object.md)
* [オブジェクト コレクション](object-collection.md)
* [Billboard と Tag-along](billboarding-and-tag-along.md)
