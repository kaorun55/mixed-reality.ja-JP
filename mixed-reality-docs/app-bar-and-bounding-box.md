---
title: アプリ バー、境界ボックス
description: アプリ バーは、一連のホログラムの範囲の下端に表示されるボタンを含むオブジェクト レベルのメニューです。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality アプリ バー、境界ボックス
ms.openlocfilehash: bdce92e00193230d1f7a487f11ef0487f1d6657c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602081"
---
# <a name="bounding-box-and-app-bar"></a>境界ボックスと、アプリ バー
![境界は、複合現実でのオブジェクトの操作の標準的なインターフェイスです。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>境界ボックスとは何ですか。

境界は、複合現実でのオブジェクトの操作の標準的なインターフェイスです。 オブジェクトが現在調整可能である、アフォー ダンス、ユーザーを提供します。 角に丸みオブジェクトが拡張できるもユーザーに通知します。 この visual アフォー ダンスでは、調整モードの外部で表示されていない場合でも、ユーザーが – オブジェクトの合計領域に表示します。 これは、機能は、別のオブジェクトまたは画面を基準としてスナップされます。 オブジェクトが動作であることを周囲のスペースがあったかのように見えるがなかった場合ため特に重要です。 HoloLens 2 では、境界ボックスは、ユーザーの指の近くに応答します。 オブジェクトからの距離を認識する視覚的なフィードバックが表示されます。 

![HoloLens ビューがポイントの境界ボックスを使用してオブジェクトのスケーリング](images/bounding-box-scale.gif)<br>
*境界ボックスを使用してオブジェクトのスケーリング*

境界ボックスのキューブのような角では、スケールを調整するために広く理解されているパターンに従います。 結合「調整モード」にオブジェクトを配置の明示的なアクションでできます両方オブジェクトの移動しますが、それぞれの環境でスケールも明らかです。

![HoloLens ビューがポイントの境界ボックスを使用してオブジェクトを回転します。](images/bounding-box-rotate.gif)<br>
*境界ボックスを使用して、オブジェクトの回転*

境界ボックスの端に球アフォーとは、回転のインジケーターです。 これにより、ユーザーは、配置されたホログラム経由で細かい調整をできるようにします。 だけでなく、調整およびできます、スケールしますが、も回転させるようになりました。

* Unity アプリ開発では、次を参照してください[Mixed Reality Toolkit Unity での境界ボックス。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="what-is-the-app-bar"></a>アプリ バーとは何ですか。

アプリ バーは、一連のホログラムの範囲の下端に表示されるボタンを含むオブジェクト レベルのメニューです。 このパターンは、通常ユーザーを削除し、ホログラムを調整できるように使用されます。

このパターンはユーザーがオブジェクトの周囲に移動すると、ロックされている世界であるオブジェクトで使用されるため、アプリ バーは、ユーザーに最も近いオブジェクトの側で常に表示されます。 結果は同じ効果的にこのいないビルボード処理中に実現します。ユーザーの位置がや各自の環境内の別の場所から使用されないようにブロックの機能を防止します。

![ホログラムを歩きします。 アプリ バーに従います。](images/holobar-followuser.gif)<br>
*ホログラムを歩きながら、アプリ バーに依存します。*

アプリ バーは、主にユーザーの環境で配置されたオブジェクトを管理する手段として設計されています。 境界ボックスと組み合わせて、ユーザーは、複合現実でのオブジェクトを指向場所と方法を完全に制御を持ちます。

* Unity アプリ開発では、次を参照してください[Mixed Reality Toolkit Unity でのアプリ バー。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>関連項目
* [境界ボックス Mixed Reality Toolkit Unity で](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)
* [アプリ バー Mixed Reality Toolkit Unity で](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)
* [対話型のオブジェクト](interactable-object.md)
* [Unity 内のテキスト](text-in-unity.md)
* [オブジェクトのコレクション](object-collection.md)
* [進行状況の表示](progress.md)
