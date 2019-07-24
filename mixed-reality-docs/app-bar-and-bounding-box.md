---
title: 境界ボックスとアプリバー
description: アプリバーは、ホログラムの境界の下端に表示される一連のボタンを含むオブジェクトレベルのメニューです。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality、アプリバー、境界ボックス
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829678"
---
# <a name="bounding-box-and-app-bar"></a>境界ボックスとアプリバー
![境界は、混合現実のオブジェクト操作の標準インターフェイスです。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>境界ボックスとは何ですか。

境界は、混合現実のオブジェクト操作の標準インターフェイスです。 これにより、オブジェクトが現在調整可能であることを示す affordance がユーザーに提供されます。 コーナーは、オブジェクトのスケールも可能であることをユーザーに通知します。 このビジュアル affordance は、オブジェクトの合計領域をユーザーに表示します (調整モード以外では表示されません)。 これは特に重要です。存在しない場合は、別のオブジェクトまたはサーフェイスにスナップされたオブジェクトが、そこに存在しない領域があるかのように動作しているように見えることがあります。 HoloLens 2 では、境界ボックスはダイレクト操作と連動し、ユーザーの finger's 近接に応答します。 これは、ユーザーがオブジェクトからの距離を認識するのに役立つ視覚的フィードバックを示しています。 

![境界ボックスを使用したオブジェクトのスケーリングの HoloLens ポイント](images/HoloLens2_BoundingBox.gif)<br>
*境界ボックスを使用したオブジェクトのスケーリング*

境界ボックスの隅にあるハンドルは、スケールを調整するために広く理解されているパターンに従います。 

![境界ボックスを使用してオブジェクトを回転するための HoloLens のポイント](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*境界ボックスを使用したオブジェクトの回転*


![手書きの視覚的フィードバック](images/HoloLens2_Proximity.gif)<br>
*近接度に基づくビジュアルフィードバック*

境界ボックスの端の垂直四角形 affordances は回転インジケーターです。 これにより、ユーザーは、配置されたホログラムをより細かく調整できます。 調整と拡大縮小だけでなく、回転も可能になりました。

* Unity アプリの開発については、「 [Mixed Reality Toolkit の境界ボックス-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 」を参照してください。



## <a name="what-is-the-app-bar"></a>アプリバーとは何ですか。

アプリバーは、ホログラムの境界の下端に表示される一連のボタンを含むオブジェクトレベルのメニューです。 このパターンは、ユーザーがホログラムを削除して調整できるようにするためによく使用されます。

このパターンは、世界でロックされているオブジェクトで使用されるため、ユーザーがオブジェクトの周りを移動すると、アプリバーは常にユーザーに最も近いオブジェクトの側に表示されます。 これは billboarding ではありませんが、実質的に同じ結果を実現します。環境内の別の場所から使用できるようにするために、ユーザーの位置を occlude またはブロックすることを防止します。

![ホログラムの周りを歩いています。 アプリバーは次のようになります。](images/HoloLens2_AppBarFollowing.gif)<br>
*ホログラムの周りをたどると、アプリバーは次のようになります。*

アプリバーは、主にユーザーの環境で配置されたオブジェクトを管理する方法として設計されました。 境界ボックスと組み合わせて使用すると、ユーザーはどこでも、どのようにオブジェクトが混合現実に向いているかを完全に制御できます。

* Unity アプリの開発については、「 [Mixed Reality Toolkit のアプリバー-unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) 」を参照してください。

## <a name="see-also"></a>関連項目
* [対話可能なオブジェクト](interactable-object.md)
* [Unity のテキスト](text-in-unity.md)
* [オブジェクト コレクション](object-collection.md)
* [進行状況を表示する](progress.md)
