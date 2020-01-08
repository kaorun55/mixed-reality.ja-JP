---
title: 入門チュートリアル-4. 動的なコンテンツの配置とソルバーの使用
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, チュートリアル, hololens
ms.openlocfilehash: e08de0bc769ceda493eafe40158b6aeed87751c7
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334360"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. 動的なコンテンツを配置し、ソルバーを使用する

ホログラムは、ユーザーに直感的に従うことができ、シームレスで洗練された方法で物理的な環境に配置されると、HoloLens 2 で有効になります。 このチュートリアルでは、複雑な空間配置シナリオを解決するために、MRTK の利用可能な配置ツール (ソルバー) を使用して、ホログラムを動的に配置する方法について説明します。 MRTK では、ソルバーはスクリプトと動作のシステムであり、UI 要素がシーン内のユーザー、ユーザー、またはその他のゲームオブジェクトに従うことを許可するために使用されます。 また、特定の場所にすばやくスナップして、アプリケーションをさらに直感的にするために使用することもできます。

## <a name="objectives"></a>目標

* MRTK ソルバーの紹介
* ソルバーを使用して、ボタン コレクションにユーザーを追跡させる
* ソルバーを使用して、追跡されているユーザーの手をゲーム オブジェクトに追跡させる

## <a name="location-of-solvers-in-the-mrtk"></a>MRTK でのソルバーの場所

 プロジェクトで使用可能なソルバーを見つけるには、MRTK SDK フォルダー (MixedRealityToolkit フォルダー) を探します。 次の図に示すように、utilities フォルダーの下に、ソルバーフォルダーが表示されます。

![ソルバー](images/lesson3_chapter1_step1im.PNG)

>[!NOTE]
>このレッスンでは、回転ソルバーと放射 Alview ソルバーの実装についてのみ説明します。 MRTK で利用可能なすべての種類のソルバーの詳細については、次のページを参照してください: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="use-a-solver-to-follow-the-user"></a>ソルバーを使用してユーザーを追跡する

この章の目的は、以前に作成されたボタンコレクションを拡張して、ユーザーの見つめ方向に従うようにすることです。 以前のバージョンの MRTK と HoloToolkit では、これは tagalong いう機能と呼ばれていました。

1. 以前のレッスンから、[Button Collection] (ボタン コレクション) 親オブジェクトを選択します。

    ![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. [インスペクター] パネルで [コンポーネントの追加] ボタンをクリックし、回転を検索します。 回転コンポーネントが表示されます。 これを選択して、回転コンポーネントをボタンコレクションゲームオブジェクトに追加します。

    ![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

    >[!NOTE]
    >回転コンポーネントを追加すると、システムによって、必要なコンポーネントである、"要素の追加" コンポーネントも追加されることがわかります。

3. ユーザーに従うようにボタンコレクションを構成するには、次の調整を実装する必要があります (以下の図を参照してください)。

    * 回転スクリプトで、[方向の種類] ボックスの一覧を [ヨーのみ] に設定します。 これを設定するのは、ユーザーを追跡する際にオブジェクトの 1 つの軸だけが回転するようにするためです。
    * すべての軸で [Local Offset] (ローカル オフセット) を 0 に設定します。 ワールドオフセットを x = 0、y =-0.1、z = 0.6 に設定します。 これにより、オブジェクトの移動がロックされるため、ユーザーが高さを変更したときに、ユーザーが環境について移動したときにユーザーの操作を継続できるようになります。 これらの値を調整して、さまざまな動作を実現できます。
    * ユーザーが十分に離れたところでボタンがユーザーのビューに従うようにするには、次のように、[ワールドオフセットの角度をステップ実行する] チェックボックスをオンにします (注: このタイトルは、次の図のように、一部の画面では切り捨てられる場合があります)。たとえば、オブジェクトが90度ごとにユーザーにのみ従うようにするには、ステップ数を4に設定します (下の例では緑色の矢印でマークされています)。

    ![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

## <a name="enabling-objects-to-follow-tracked-hands"></a>追跡したハンドに従ってオブジェクトを有効にする

このセクションでは、前に作成したキューブゲームオブジェクトを構成して、ユーザーの追跡対象ユーザーに対して、放射 Alview ソルバーを使用します。

1. BaseScene 階層内のキューブオブジェクトを選択します。 [インスペクター] パネルの [コンポーネントの追加] をクリックします。 検索ボックスに「」と入力し、[放射型] コンポーネントを選択してキューブに追加します。 また、このキューブには、パーティションコンポーネントが自動的に追加されます。

    ![mrlearning-base-ch3-3-step3](images/mrlearning-base-ch3-3-step1.png)

2. ヘッドではなく手の形になるように放射 Alview を変更するには、[追跡対象の種類] オプションの横にあるドロップダウンメニューを選択し、メニューから [手の接合] を選択します。

    ![mrlearning-base-ch3-3-step2](images/mrlearning-base-ch3-3-step2a.png)

    これで、2つの新しいオプションである [追跡された人の種類] と [追跡された手の継手] が表示されます。 この例では、次の図に示すように、左側の手首に従います。

    ![mrlearning-base-ch3-3-step2b](images/mrlearning-base-ch3-3-step2b.png)

3. 放射状ビューの最大距離と最小距離を0に設定します。これにより、キューブがユーザーの手首と同じ距離になることはありません。 設定すると、cube は完全に手首を追従するようになります。 また、[参照方向] フィールドを調整して、キューブの向きの動作を調整することもできます。たとえば、オブジェクトをオブジェクト指向に設定することによって、ユーザーの手首でオブジェクトを回転できるようにする場合などです。

    ![mrlearning-base-ch3-3-step3](images/mrlearning-base-ch3-3-step3.png)

## <a name="congratulations"></a>結論

このチュートリアルでは、MRTK のソルバーを使用して、UI を直感的にユーザーに従う方法を学習しました。 また、ソルバーをゲーム オブジェクト (cube) に追加して、ユーザーの追跡対象の手を追跡させる方法についても学びました。 MRTK に含まれるこれらのソルバーや他のソルバーについて学ぶには、[MRTK ソルバーに関するドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)を参照してください。

[次のレッスン: 5. 3D オブジェクトとの対話](mrlearning-base-ch4.md)
