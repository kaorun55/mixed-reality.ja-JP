---
title: アプリ バー、境界ボックス
description: アプリ バーは、一連のホログラムの範囲の下端に表示されるボタンを含むオブジェクト レベルのメニューです。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality アプリ バー、境界ボックス
ms.openlocfilehash: ab472e1c988e6bdfb0a69d90e90280082b3db759
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813859"
---
# <a name="bounding-box-and-app-bar"></a>境界ボックスと、アプリ バー
![境界は、複合現実でのオブジェクトの操作の標準的なインターフェイスです。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>境界ボックスとは何ですか。

境界は、複合現実でのオブジェクトの操作の標準的なインターフェイスです。 オブジェクトが現在調整可能である、アフォー ダンス、ユーザーを提供します。 角に丸みオブジェクトが拡張できるもユーザーに通知します。 この visual アフォー ダンスでは、調整モードの外部で表示されていない場合でも、ユーザーが – オブジェクトの合計領域に表示します。 これは、機能は、別のオブジェクトまたは画面を基準としてスナップされます。 オブジェクトが動作であることを周囲のスペースがあったかのように見えるがなかった場合ため特に重要です。 HoloLens 2 は、境界ボックスは、直接手操作と連携し、ユーザーの指の近くに応答します。 オブジェクトからの距離を認識するユーザーを支援する視覚的なフィードバックが表示されます。 

![HoloLens ビューがポイントの境界ボックスを使用してオブジェクトのスケーリング](images/HoloLens2_BoundingBox.gif)<br>
*境界ボックスを使用してオブジェクトのスケーリング*

境界ボックスの角のハンドルでは、スケールを調整するために広く理解されているパターンに従います。 

![HoloLens ビューがポイントの境界ボックスを使用してオブジェクトを回転します。](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*境界ボックスを使用して、オブジェクトの回転*


![近接の手の形で視覚的なフィードバック](images/HoloLens2_Proximity.gif)<br>
*近接度に基づいて視覚的なフィードバック*

境界ボックスの端に垂直方向の長方形アフォーとは、回転のインジケーターです。 これにより、ユーザーは、配置されたホログラム経由で細かい調整をできるようにします。 だけでなく、調整およびできます、スケールしますが、も回転させるようになりました。

* Unity アプリ開発では、次を参照してください[Mixed Reality Toolkit Unity での境界ボックス。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)



## <a name="what-is-the-app-bar"></a>アプリ バーとは何ですか。

アプリ バーは、一連のホログラムの範囲の下端に表示されるボタンを含むオブジェクト レベルのメニューです。 このパターンは、通常ユーザーを削除し、ホログラムを調整できるように使用されます。

このパターンはユーザーがオブジェクトの周囲に移動すると、ロックされている世界であるオブジェクトで使用されるため、アプリ バーは、ユーザーに最も近いオブジェクトの側で常に表示されます。 結果は同じ効果的にこのいないビルボード処理中に実現します。ユーザーの位置がや各自の環境内の別の場所から使用されないようにブロックの機能を防止します。

![ホログラムを歩きします。 アプリ バーに従います。](images/HoloLens2_AppBarFollowing.gif)<br>
*ホログラムを歩きながら、アプリ バーに依存します。*

アプリ バーは、主にユーザーの環境で配置されたオブジェクトを管理する手段として設計されています。 境界ボックスと組み合わせて、ユーザーは、複合現実でのオブジェクトを指向場所と方法を完全に制御を持ちます。

* Unity アプリ開発では、次を参照してください[Mixed Reality Toolkit Unity でのアプリ バー。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>関連項目
* [対話可能なオブジェクト](interactable-object.md)
* [Unity のテキスト](text-in-unity.md)
* [オブジェクト コレクション](object-collection.md)
* [進行状況を表示する](progress.md)
