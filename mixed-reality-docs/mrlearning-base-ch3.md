---
title: MR 学習ベース モジュール - ダイナミック コンテンツの配置とソルバー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, チュートリアル, hololens
ms.openlocfilehash: 6f05b2cecd388b1b2f13e7e5228bc90091eee3bd
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66270399"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a>MR 学習ベース モジュール - ダイナミック コンテンツの配置とソルバー

ホログラムは HoloLens 2 で現実のものとなります。ホログラムは直感的にユーザーを追跡し、滑らかで洗練された操作ができるように物理環境に配置されます。 レッスン 3 では、「ソルバー」として知られる MRTK で使用できる配置ツールを使用して、ホログラムを動的に配置する方法について学習します。 「ソルバー」と呼ばれているのは、複雑な空間配置アルゴリズムを解決することができるからです。 MRTK では、ソルバーとは、UI 要素がシーン内で自分、ユーザー、他のゲーム オブジェクトを追跡できるようにするために使用する、スクリプトと動作のシステムです。 また、特定の場所にすばやくスナップして、アプリケーションをさらに直感的にするために使用することもできます。 

## <a name="objectives"></a>目標

* MRTK ソルバーの紹介
* ソルバーを使用して、ボタン コレクションにユーザーを追跡させる
* ソルバーを使用して、追跡されているユーザーの手をゲーム オブジェクトに追跡させる

## <a name="instructions"></a>手順

### <a name="location-of-solvers-in-the-mrtk"></a>MRTK でのソルバーの場所
 自分のプロジェクト内で利用できるソルバーを見つけるには、次の図に示されているように、MRTK SDK フォルダー ([MixedRealityToolkit.SDK] フォルダー) の [Utilities] (ユーティリティ) フォルダー内の [Solvers] (ソルバー) フォルダーを確認します。

![ソルバー](images/lesson3_chapter1_step1im.PNG)

>注:このレッスンでは、"Orbital" ソルバーと "RadialView" ソルバーのみの実装について説明します。 MRTK で利用できるすべてのソルバーについて学ぶには、次を参照してください。 https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>ソルバーを使用してユーザーを追跡する
この章の目標は、ユーザーの視線の方向を追跡するものとして以前に作成したボタン コレクションを強化することです。 以前のバージョンの MRTK と HoloToolkit では、"taglong" 機能と呼ばれていました。

1. 以前のレッスンから、[Button Collection] (ボタン コレクション) 親オブジェクトを選択します。

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. [Inspector] (インスペクター) パネルで、[Add Component] (コンポーネントの追加) ボタンをクリックして、「orbital」を検索します。 [Orbital] コンポーネントが表示されます。 これを選択して、[Button Collection] (ボタン コレクション) ゲーム オブジェクトに [Orbital] コンポーネントを追加します。

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

>注:コンポーネントを追加すると、システムにより [Inspector] (インスペクター) タブに [Orbital (Script)] と [Solver Handler (Script)] が追加されます。これは必須コンポーネントです。 

3. ユーザーを追跡するようボタン コレクションを構成するには、以下の調整を実装する必要があります (下の図も参照してください)。
- [Orbital (Script)] で、[Orientation Type] (向きタイプ) ドロップダウン リストを [Yaw Only] (ヨーのみ) に設定します。 これを設定するのは、ユーザーを追跡する際にオブジェクトの 1 つの軸だけが回転するようにするためです。
- すべての軸で [Local Offset] (ローカル オフセット) を 0 に設定します。 [World Offset] (ワールド オフセット) を、x = 0、y = -0.1、z = 0.6 に設定します。 こうすることでオブジェクトの動きを次のように固定できます。つまり、ユーザーが高さを変えると、オブジェクトは物理環境内で固定された高さにとどまりながら、ユーザーが環境内で移動する際にユーザーを追跡することができます。 これらの値を調整して、さまざまな動作を実現できます。
- ユーザーが頭を大きく回転させた後、ボタンがユーザーの視界だけを追跡する動作の場合、[Use Angle Stepping for world offset] (ワールド オフセットに角度のステップを使用する) チェックボックスを選択できます (注意: 次の図と同じように、画面によってはこのテキストは一部表示されません)。たとえば、オブジェクトに 90 度ごとにユーザーを追跡させるには、ステップの数を 4 に設定します (左の例で緑の矢印で示されている)。 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>オブジェクトに追跡対象の手を追跡させる

このセクションでは、RadialView ソルバーを使用してユーザーの追跡対象の手を追跡するために、以前に作成した cube ゲーム オブジェクトを構成します。

1. [BaseScene] 階層内で [Cube] オブジェクトを選択します。 [Inspector] (インスペクター) パネルで、[Add Component] (コンポーネントの追加) をクリックします。 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. 検索ボックスで「RadialView」と入力し、[RadialView] コンポーネントを選択して cube に追加します。 [Solver Handler] コンポーネントも自動で cube に追加されます。

3. ラジアル ビューを、頭ではなく左手を追跡するように変更します。 [tracked object to reference] (参照する追跡対象オブジェクト) オプションの隣にあるドロップダウン メニューを選択します。 メニューから [Hand Joint Left] (左手の関節) を選択します。

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. 手の関節を選択したら、cube に追跡させる手の部分を選択できます。 この例では、手首を使います。 [tracked hand joint] (追跡対象の手の関節) オプションの隣にあるドロップダウン メニューから、[wrist] (手首) を選択します。 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. cube とユーザーの手首との間隔がなくなるように、最小距離と最大距離を 0 に設定します。 設定すると、cube は完全に手首を追従するようになります。 また、[Reference Direction] (リファレンスの方向) フィールドを調整して、cube の方向付けに関する動作を調整することもできます (たとえば、ユーザーの手首に合わせてオブジェクトを回転させる場合、リファレンスの方向を [Orient with Tracked Object] (追跡対象オブジェクトに合わせて方向付け) に設定します)。

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a>結論
これで終了です。 このレッスンでは、MRTK ソルバーを使用して UI に直感的にユーザーを追跡させる方法を学びました。 また、ソルバーをゲーム オブジェクト (cube) に追加して、ユーザーの追跡対象の手を追跡させる方法についても学びました。 MRTK に含まれるこれらのソルバーや他のソルバーについて学ぶには、[MRTK ソルバーに関するドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)を参照してください。

[次のレッスン:3D オブジェクトの操作](mrlearning-base-ch4.md)

