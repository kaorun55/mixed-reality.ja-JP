---
title: MR 学習ベース モジュール - ダイナミック コンテンツの配置とソルバー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 401c667ef80042da9182b7f4e065dfd6884cf061
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485690"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4。動的なコンテンツの配置とソルバーの使用

ホログラムは HoloLens 2 で現実のものとなります。ホログラムは直感的にユーザーを追跡し、滑らかで洗練された操作ができるように物理環境に配置されます。 このチュートリアルでは、複雑な空間配置のシナリオを解決するために、ソルバーと呼ばれる MRTK の利用可能な配置ツールを使用して、ホログラムを動的に配置する方法について説明します。 MRTK では、ソルバーはスクリプトと動作のシステムであり、UI 要素がシーン内のユーザー、ユーザー、またはその他のゲームオブジェクトに従うことを許可するために使用されます。 また、特定の場所にすばやくスナップして、アプリケーションをさらに直感的にするために使用することもできます。 

## <a name="objectives"></a>目的

* MRTK ソルバーの紹介
* ソルバーを使用して、ボタン コレクションにユーザーを追跡させる
* ソルバーを使用して、追跡されているユーザーの手をゲーム オブジェクトに追跡させる

## <a name="instructions"></a>手順

### <a name="location-of-solvers-in-the-mrtk"></a>MRTK でのソルバーの場所
 自分のプロジェクト内で利用できるソルバーを見つけるには、次の図に示されているように、MRTK SDK フォルダー ([MixedRealityToolkit.SDK] フォルダー) の [Utilities] (ユーティリティ) フォルダー内の [Solvers] (ソルバー) フォルダーを確認します。

![ソルバー](images/lesson3_chapter1_step1im.PNG)

>注:このレッスンでは、回転ソルバーと放射 Alview ソルバーの実装についてのみ説明します。 MRTK で利用できるすべてのソルバーについて学ぶには、次を参照してください。 https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>ソルバーを使用してユーザーを追跡する
この章の目的は、以前に作成されたボタンコレクションを拡張して、ユーザーの見つめ方向に従うようにすることです。 MRTK と HoloToolkit の以前のバージョンでは、これは tagalong いう機能と呼ばれていました。

1. 以前のレッスンから、[Button Collection] (ボタン コレクション) 親オブジェクトを選択します。

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. [インスペクター] パネルで [コンポーネントの追加] ボタンをクリックし、回転を検索します。 [Orbital] コンポーネントが表示されます。 これを選択して、[Button Collection] (ボタン コレクション) ゲーム オブジェクトに [Orbital] コンポーネントを追加します。

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

>注:コンポーネントを追加すると、システムにより [Inspector] (インスペクター) タブに [Orbital (Script)] と [Solver Handler (Script)] が追加されます。これは必須コンポーネントです。 

3. ユーザーに従うようにボタンコレクションを構成するには、次の調整を実装する必要があります (以下の図を参照してください)。
- 回転スクリプトで、[方向の種類] ボックスの一覧を [ヨーのみ] に設定します。 これを設定するのは、ユーザーを追跡する際にオブジェクトの 1 つの軸だけが回転するようにするためです。
- すべての軸で [Local Offset] (ローカル オフセット) を 0 に設定します。 [World Offset] (ワールド オフセット) を、x = 0、y = -0.1、z = 0.6 に設定します。 こうすることでオブジェクトの動きを次のように固定できます。つまり、ユーザーが高さを変えると、オブジェクトは物理環境内で固定された高さにとどまりながら、ユーザーが環境内で移動する際にユーザーを追跡することができます。 これらの値を調整して、さまざまな動作を実現できます。
- ユーザーが自分のヘッドの位置を十分に変えた後に、ボタンがユーザーのビューにのみ表示されるようにするための動作については、[ワールドオフセットの角度をステップ実行する] チェックボックスをオンにすることができます (注:次の図と同じように、画面によってはこのテキストは一部表示されません)。たとえば、オブジェクトに 90 度ごとにユーザーを追跡させるには、ステップの数を 4 に設定します (左の例で緑の矢印で示されている)。 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>追跡したハンドに従ってオブジェクトを有効にする

このセクションでは、RadialView ソルバーを使用してユーザーの追跡対象の手を追跡するために、以前に作成した cube ゲーム オブジェクトを構成します。

1. [BaseScene] 階層内で [Cube] オブジェクトを選択します。 [インスペクター] パネルの [コンポーネントの追加] をクリックします。 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. 検索ボックスに「」と入力し、[放射型] コンポーネントを選択してキューブに追加します。 [Solver Handler] コンポーネントも自動で cube に追加されます。

3. ラジアル ビューを、頭ではなく左手を追跡するように変更します。 [参照するオブジェクトの追跡] オプションの横にあるドロップダウンメニューを選択します。 メニューから [手の接合] を選択します。

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. 手の関節を選択したら、cube に追跡させる手の部分を選択できます。 この例では、手首を使います。 [追跡されたハンドジョイント] オプションの横にあるドロップダウンメニューを選択し、[手首] を選択します。 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. cube とユーザーの手首との間隔がなくなるように、最小距離と最大距離を 0 に設定します。 設定すると、cube は完全に手首を追従するようになります。 また、[参照方向] フィールドを調整して、キューブの向きの動作を調整することもできます。たとえば、オブジェクトをユーザーの手首で回転できるようにする場合は、参照の方向を [追跡対象オブジェクト] に設定します。

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

## <a name="congratulations"></a>結論
このチュートリアルでは、MRTK のソルバーを使用して、UI を直感的にユーザーに従う方法を学習しました。 また、ソルバーをゲーム オブジェクト (cube) に追加して、ユーザーの追跡対象の手を追跡させる方法についても学びました。 MRTK に含まれるこれらのソルバーや他のソルバーについて学ぶには、[MRTK ソルバーに関するドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)を参照してください。

[次のレッスン:5。  3D オブジェクトの操作](mrlearning-base-ch4.md)

