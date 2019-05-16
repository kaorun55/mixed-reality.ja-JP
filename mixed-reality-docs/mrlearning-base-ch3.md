---
title: 動的なコンテンツの配置とソルバー MR Learning ベース モジュール
description: このコースでは、複合現実のアプリケーション内で Azure の顔認識機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 複合現実、unity、チュートリアル、hololens
ms.openlocfilehash: 04ed2217c473c5649c1850fcc757d866e23b9b56
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730895"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a>動的なコンテンツの配置とソルバー MR Learning ベース モジュール

ホログラム、生きるように、HoloLens 2 で直感的に、ユーザーをフォローし、相互作用は、シームレスかつ洗練された方法で、物理環境に配置されます。 レッスン 3 では「ソルバー」と呼ばれる MRTK の使用可能な配置ツールを使用してホログラムを動的に配置する方法について説明します。 これらは、複雑な空間配置アルゴリズムを解決する方法を「ソルバー」と呼ばれます。 MRTK ソルバーは、システムのスクリプトと動作をフォローして、ユーザーまたはその他のゲーム オブジェクト、シーン内の UI 要素を許可するようにするために使用します。 こともできますを迅速に特定の位置にスナップより直感的なアプリケーションを作成します。 

## <a name="objectives"></a>目標

* MRTK のソルバーを紹介します。
* ボタンのコレクションにソルバーを使用して、ユーザーをフォローします。
* ゲーム オブジェクトを持つソルバーを使用して次のユーザーの追跡対象の手

## <a name="instructions"></a>手順

### <a name="location-of-solvers-in-the-mrtk"></a>MRTK ソルバーの場所
 次の図に示すように、プロジェクトで使用可能なソルバーを検索、utilities フォルダーの下で、MRTK SDK フォルダー (MixedRealityToolkit.SDK フォルダー) で検索するには、ソルバー フォルダーが表示されます。

![ソルバー](images/lesson3_chapter1_step1im.PNG)

>注:このレッスンでは、「回転のこぎり」ソルバーおよび"RadialView"ソルバーの実装を上回ることが変わりますのみ。 ソルバー、MRTK で使用できるさまざまなについての詳細についてには、以下を参照してください。 https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>問題を解くプログラムを使用して、ユーザーをフォローするには
この章の目的は、ように、ユーザーの視線方向続くに以前に作成したボタンのコレクションを強化するためにです。 MRTK と HoloToolkit の以前のバージョンでこの、"taglong"機能としてに呼ばれていました。

1. 前のレッスンからボタン コレクションの親オブジェクトを選択します。

![Lesson3 第 2 章 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. Inspector パネルで、「させます。」の検索と"コンポーネントの追加 ボタンをクリックします。 回転のこぎりコンポーネントが表示されます。 回転のこぎりコンポーネントをボタン コレクションのゲーム オブジェクトに追加することを選択します。

![Lesson3 第 2 章 Step2im](images/Lesson3_Chapter2_step2im.PNG)

>注:コンポーネントを追加すると、システムが inspector タブで、必要なコンポーネントである、回転のこぎりスクリプトおよびソルバー ハンドラー スクリプトを追加することがわかります。 

3. 次の調整を実装するのユーザーをフォローするボタンのコレクションを構成するには (くださいは次の図も参照)。
- 回転のこぎりのスクリプトでは、「ヨーのみです。」を「向きの種類」のドロップダウン リストを設定します。 これにより、ユーザーを次のように、オブジェクトの 1 つだけその軸が回転するため。
- すべての軸で、ローカルのオフセットを 0 に設定します。 X に世界中のオフセットを設定 = 0、y =-0.1 と z = 0.6 です。 これにより、オブジェクトは、環境に関するユーザーが移動すると、ユーザーに従うことを許可する一方で、物理環境、高さを固定する引き続き高さを変更するときなど、オブジェクトの移動がロックされます。 Wade 一連の動作を実現するために、これらの値を調整することがあります。
- これにより、ボタンのみ後で次のユーザーのビュー、ユーザーが自分の頭が十分にに従って動作するためには、「の世界のオフセット角度ステップを使用して」チェック ボックスをオン可能性があります (注。このタイトル可能性がありますに切り捨てる一部の画面では、下の画像であるためです。)たとえば、ユーザー-90 にのみ、オブジェクトには、設定ステップ数 (左側の例では、緑色の矢印でマークされた) 4 に等しい。 

![Lesson3 第 2 章 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>追跡対象の手に従うオブジェクトの有効化

このセクションでは、以下の RadialView ソルバーを使用して、ユーザーの追跡対象の手に以前に作成したキューブのゲーム オブジェクトを構成します。

1. BaseScene 階層では、キューブ オブジェクトを選択します。 Inspector パネルの「コンポーネントの追加」をクリックします。 

![Lesson3 第 3 章 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. "RadialView"検索ボックスに入力し、キューブに追加する RadialView コンポーネントを選択します。 ソルバーのハンドラ コンポーネントは、キューブに自動的に追加もします。

3. ヘッドに従っていないが、以下の左側にある放射状のビューを変更します。 「参照するオブジェクトを追跡」オプションの横にあるドロップダウン メニューを選択します。 メニューから「ジョイントが左を渡す」を選択します。

![Lesson3 第 3 章 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. ハンド ジョイントを選択すると、キューブにたいして手のアイコンのどの部分を選択できます。 この例では、手首を使用するでしょう。 オプションの横にあるは、「追跡手ジョイント」は、ドロップダウン メニューを選択し、手首を選択します。 

![Lesson3 第 3 章 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. キューブがユーザーのリストとの間の距離があるないように、最大および最小の距離を 0 に設定します。 一度設定すると、キューブが一直線手首をします。 場合 (たとえば、ユーザーのリストでの回転、"回転と追跡 Object"への参照の方向を設定するオブジェクトを許可するには) キューブが方向にはどのように動作を調整する「参照方向」フィールドを調整することも可能性があります。

![Lesson3 第 3 章 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a>おめでとうございます
これで終了です。 このレッスンでは、直感的に、ユーザーをフォロー ui MRTK のソルバーを使用する方法について説明しました。 次のユーザーの追跡対象の手をゲーム オブジェクト (つまり、キューブ) に問題を解くプログラムをアタッチする方法も学習しました。 これらの機能と、MRTK に含まれているその他のソルバーの詳細については、自由にアクセスしてください、 [MRTK ソルバー ドキュメント ページ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)します。

[次のレッスン:3D オブジェクトの相互作用](mrlearning-base-ch4.md)

