---
title: 入門チュートリアル-5. 3D オブジェクトとの対話
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 8c60d8291ede123817c93458fff003891169840c
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105973"
---
# <a name="5-interacting-with-3d-objects"></a>5. 3D オブジェクトとの対話

このチュートリアルでは、基本的な3D コンテンツとユーザーエクスペリエンスについて学習します。次に例を示します。

* コレクションの一部としての3D オブジェクトの整理
* 基本操作のための境界ボックス
* Near と far の相互作用
* ハンドトラッキングを使用したタッチジェスチャとグラブジェスチャ

## <a name="objectives"></a>目標

* MRTK の grid オブジェクトコレクションで3D コンテンツを整理する方法について説明します。
* 境界ボックスを実装する
* 基本的な操作のための3D オブジェクトの構成--移動、回転、およびスケール
* 近距離操作と遠距離操作について確認する
* グラブやタッチなど、その他のハンドトラッキングジェスチャについて説明します。

## <a name="instructions"></a>手順

### <a name="organizing-3d-objects-in-a-collection"></a>3D オブジェクトをコレクションに整理する

1. 階層を右クリックし、[空の作成] を選択して空の game オブジェクトを作成し、名前を3DObjectCollection に変更して、x = 0、y = 0、z = 0 に配置されていることを確認します。

    ![mrlearning-base-ch4-1-step1](images/mrlearning-base-ch4-1-step1.png)

2. Unity パッケージ HoloLens2 をダウンロードし、[レッスン1から](mrlearning-base-ch1.md)に記載されているカスタムパッケージをインポートする場合と同じ手順を使用して[2.1.0.0](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)をインポートします。 このパッケージには、このチュートリアル全体で使用される3D モデルとその他の便利なアセットが含まれています。

3. [プロジェクト] パネルで、[資産 > BaseModuleAssets] > ベースモジュール Prefabs に移動し、"不完全" を検索します。これらの Prefabs の一部を使用します。

    ![mrlearning-base-ch4-1-step3](images/mrlearning-base-ch4-1-step3.png)

4. コーヒーカップを手順 1. の 3DObjectCollection game オブジェクトにドラッグします。 これでコーヒー カップはコレクションの子になりました。

    ![mrlearning-base-ch4-1-step4](images/mrlearning-base-ch4-1-step4.png)

5. 次に、前の手順と同じプロセスに従って、3D オブジェクトをシーンに追加します。 この例で追加するオブジェクトの一覧を次に示します。 オブジェクトを追加すると、さまざまなサイズのシーンにオブジェクトが表示されることがあります。 [インスペクター] パネルの [変換の設定] で、各3D モデルのスケールを調整します。 この例で推奨される調整とそのオブジェクトを以下に示します。

    * Cheese_BaseModuleIncomplete。 Scale: x = 0.05、y = 0.05、z = 0.05。
    * CoffeeCup_BaseModuleIncomplete。 Scale: x = 0.1、y = 0.1、z = 0.1。
    * EarthCore_BaseModuleIncomplete。 Scale: x = 50.0 y = 50.0、z = 50.0。
    * Model_Platonic_BaseModuleIncomplete。 Scale: x = 0.13、y = 0.13、z = 0.13。
    * Octa_BaseModuleIncomplete。 Scale: x = 0.13。 y = 0.13、z =0.13 に設定します。
    * TheModule_BaseModuleIncomplete。 Scale: x = 0.03、y = 0.03、z = 0.03。

    ![mrlearning-base-ch4-1-step5](images/mrlearning-base-ch4-1-step5.png)

6. シーンに3つのキューブを追加します。 3DObjectCollection オブジェクトを右クリックし、[3D オブジェクト]、[キューブ] の順に選択します。 スケールを x = 0.14、y = 0.14、z = 0.14 に設定します。 合計3つのキューブを作成するには、この手順をさらに2回繰り返します。 または、キューブを合計3つのキューブに対して2回複製することもできます。 また、[アセット] > [BaseModuleAssets] > [ベース モジュール プレハブ] から用意されている 3 つの立方体のプレハブを使用し、GreenCube_BaseModuleIncomplete、BlueCube_BaseModuleIncomplete、および OrangeCube_BaseModuleIncomplete を選択することもできます。

    ![mrlearning-base-ch4-1-step6](images/mrlearning-base-ch4-1-step6.png)

7. 「[レッスン 2](mrlearning-base-ch2.md)」で説明されている手順に従って、オブジェクトのコレクションを整理してグリッドを形成します。 3 x 3 グリッドでオブジェクトを構成する例については、次の図を参照してください。

    ![mrlearning-base-ch4-1-step7](images/mrlearning-base-ch4-1-step7.png)

    >[!NOTE]
    >上の図のように、一部のオブジェクトはセンター外にあることがわかります。 これは、プレハブまたはオブジェクトに整列していない子オブジェクトが含まれている可能性があるためです。 オブジェクトの位置や子オブジェクトの位置に必要な調整を自由に加えることで、グリッドを適切に整列させることができます。

### <a name="manipulating-3d-objects"></a>3D オブジェクトの操作

1. 立方体を操作する機能を追加します。 3D オブジェクトを操作する機能を追加するには、次の手順を実行します。
    * 階層内で操作する3D オブジェクト (つまり、キューブの1つ) を選択します。
    * [コンポーネントの追加] をクリックします。
    * "操作" の検索
    * 操作ハンドラーの選択
    * 3DObjectCollection オブジェクトの下にあるすべての3D オブジェクトに対して繰り返しますが、3DObjectCollection 自体は同じではありません。
    * すべての3D オブジェクトに collider または box collider があることを確認します (コンポーネント > Box Collider を追加します)。

    ![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

    >[!NOTE]
    >操作ハンドラーは、操作時にオブジェクトがどのように動作するかの設定を調整できるコンポーネントです。 これには、特定の軸での回転、拡大縮小、移動、制約の移動が含まれます。

2. 1 つの立方体を、拡大縮小しかできないように制限します。 3DObjectCollection オブジェクトで1つのキューブを選択します。 [インスペクター] パネルで、[2 つのきき操作の種類] の横にあるドロップダウンメニューをクリックし、[スケール] を選択します。 これにより、ユーザーは立方体のサイズしか変更できなくなります。

    ![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. 立方体を区別できるように、それぞれの色を変更します。
    * [プロジェクト] パネルに移動し、MixedRealityToolkit が表示されるまで下にスクロールして、それを選択します。
    * [Standard Assets] フォルダーを選択します。
    * [素材] フォルダーをクリックします。
    * 立方体のそれぞれに異なる素材をドラッグします。

    >[!NOTE]
    >立方体には任意の色を選択できます。 この例では、glowingcyan、glowingorange、および green が使用されています。 さまざまな色を自由に試すことができます。 キューブに色を追加するには、変更するキューブをクリックし、その素材をキューブの [インスペクター] パネルのメッシュレンダラーの [素材] フィールドにドラッグします。

    ![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. 3DObjectCollection オブジェクト内の別のキューブを選択し、その移動を先頭からの固定距離に制限するように設定します。 この操作を行うには、[移動] ラベルの [制約] の右側にあるドロップダウンメニューをクリックし、[ヘッドからの距離を修正] を選択します。 これにより、キューブがビジョンのフィールド内になるように調整されます。

    ![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

    次のいくつかの手順の目的は、3D オブジェクトをグラブして操作し、異なる操作設定を適用できるようにすることです。

5. [チーズ] オブジェクトを選択し、[インスペクター] パネルの [コンポーネントの追加] をクリックします。

6. [検索] ボックスで [Near インタラクション Grabbable] を検索し、スクリプトを選択します。 このコンポーネントを使用すると、ユーザーは追跡したハンドを使用してオブジェクトに接続し、オブジェクトを取得できます。 次の画像の緑色の円で示されているように、[Far 操作を許可する] チェックボックスをオフにしない限り、オブジェクトを距離から操作することもできます。

    ![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. これらのオブジェクトに対して手順 5. と 6. を繰り返して、プラトニックオブジェクト、地球コア、旧暦モジュール、およびコーヒーカップに Near Grabbable を追加します。

8. Octa オブジェクトから遠距離操作ができないようにします。 これを行うには、階層内で Octa を選択し、[far 操作を許可する] チェックボックスをオフにします (緑色の円でマークされています)。 これにより、ユーザーは追跡したハンドを使用して、octa だけを直接操作できるようになります。

    >[!NOTE]
    >操作ハンドラーコンポーネントとそれに関連する設定の完全なドキュメントについては、 [Mrtk のドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)を参照してください。

9. Near の相互作用 Grabbable コンポーネントが、地球コア、太陰暦モジュール、およびコーヒーカップに追加されていることを確認します (手順7を参照)。

10. 旧暦モジュールの場合は、次の図に示すように、操作ハンドラーの設定を変更して、オブジェクトの中心を前後の対話の両方で回転させます。

    ![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11. 地球コアの場合は、リリース動作を何も変更しません。 これにより、地球コアがユーザーのつかみから解放されると、移動は続行されません。

    ![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

    >[!NOTE]
    >この設定は、スローできるボールを作成するなどのシナリオに役立ちます。 適切なベロシティと角速度を維持して、ボールがリリースされた後も、そのボールがリリースされた速度で移動し続けます。物理的なボールの動作と似ています。

### <a name="adding-bounding-boxes"></a>境界ボックスの追加

境界ボックスを使用すると、直接操作 (ほぼ相互作用) と射線ベースの操作 (遠くのやり取り) の両方で、オブジェクトを1つの手で操作することが簡単になり、直観的になります。境界ボックスは、特定の軸に沿ってオブジェクトを拡大縮小および回転するために取得できるハンドルを提供します。

>[!NOTE]
>オブジェクトに境界ボックスを追加するには、まず、このレッスンで前に説明したように、オブジェクト (box collider など) に collider を用意する必要があります。 Colliders を追加するには、オブジェクトを選択し、オブジェクトの [インスペクター] パネルで [コンポーネントの追加 > Box Collider] を選択します。

1. 箱の collider を地球コアオブジェクトに追加します (まだ存在しない場合)。 指定された指示に従って、ベースモジュールの Assets フォルダーに用意されている prefab を使用する場合、box の collider とセットアップは必要ありません。 地球コアの場合、次の図に示すように、box collider を、、node_id30、地球コアの下にあるオブジェクトに追加しました。 オブジェクトの [インスペクター] タブで [node_id30] を選択し、[コンポーネントの追加] をクリックして、box collider を検索します。

    ![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

    ![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

    >[!NOTE]
    >Box collider のサイズを大きくしたり小さくしたりしないようにしてください。 それが囲むオブジェクト (この例では地球の核) とほぼ同じサイズである必要があります。 Box collider の [Collider の編集] オプションを選択して、必要に応じて box の collider を調整します。 X、y、z の値を変更するか、[エディターシーン] ウィンドウで境界ボックスハンドラーをドラッグします。

    ![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. アースコアの node_id30 オブジェクトに境界ボックスを追加します。 これを行うには、3DObjectCollection から node_id30 オブジェクトを選択します。 [インスペクター] タブで、[コンポーネントの追加] をクリックし、[境界ボックス] を検索します。 境界ボックス、ボックス コライダー、および操作スクリプト (操作ハンドラー、近距離操作 - グラブ可能) がすべて同じゲーム オブジェクト上にあることを確認します。

3. 境界ボックスの [動作] セクションで、[アクティブ化] ドロップダウンリストから [開始時にアクティブにする] を選択します。 さまざまなアクティブ化オプションおよびその他の境界ボックスオプションに関する詳細については、 [Mrtk の境界ボックスのドキュメント](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)を参照してください。

    *次のいくつかの手順では、既定のボックスマテリアル、グラブ中の素材、コーナーハンドルとサイドハンドルの視覚化を調整して、境界ボックスがどのように見えるかを変更します。MRTK には、境界ボックスをカスタマイズするためのオプションがいくつか含まれています。*

4. [プロジェクト] パネルで "boundingbox" を検索すると、次の図に示すように、検索結果に青い球で示される素材の一覧が表示されます。

5. Boundingbox マテリアルを、境界ボックスコンポーネントのボックス素材スロットにドラッグします。 また、boundingboxgrabbed の素材を取得し、境界ボックスコンポーネントのボックスに挿入します。

    ![mrlearning-base-ch4-3-step5](images/mrlearning-base-ch4-3-step5.png)

6. MRTK_BoundingBox_ScaleHandle prefab をスケールハンドル prefab スロットにドラッグし、MRTK_BoundingBox_RotateHandle prefab を結合ボックスコンポーネントの回転ハンドルスロットにドラッグします。

    ![mrlearning-base-ch4-3-step6](images/mrlearning-base-ch4-3-step6.png)

7. 境界ボックスの正しいオブジェクトを対象としていることを確認します。 境界ボックスコンポーネントには、ターゲットオブジェクトと境界オーバーライドスクリプトがあります。 境界ボックスを持つオブジェクトをこれらのスロットの両方にドラッグします。 この例では、次の図に示すように、これらのスロットの両方に node_id30 オブジェクトをドラッグします。

    ![mrlearning-base-ch4-3-step7](images/mrlearning-base-ch4-3-step7.png)

    >[!NOTE]
    >アプリケーションを起動または再生すると、オブジェクトは青いフレームで囲まれます。 そのフレームのコーナーをドラッグすると、オブジェクトのサイズを自由に変更できます。 スケーリングハンドルと回転ハンドルのサイズを大きくして表示する場合は、既定の境界ボックスの設定を使用することをお勧めします (手順 4. ~ 6. を回避)。

8. 既定の境界ボックスの視覚化に戻るには、境界ボックスのオブジェクトの [インスペクター] パネルで、回転ハンドル prefab を選択し、del キーを押して削除します。 再生モードに入ると、次の図のような境界ボックスの視覚エフェクトが表示されます。

    ![mrlearning-base-ch4-3-step8](images/mrlearning-base-ch4-3-step8.png)

    >[!NOTE]
    >境界ボックスの視覚エフェクトは、再生モードの場合にのみ表示されます。

### <a name="adding-touch-effects"></a>タッチ効果の追加

この例では、オブジェクトを手でタッチしたときに効果音が再生されるようにします。

1. ゲーム オブジェクトにオーディオ ソース コンポーネントを追加します。 シーン階層で Octa オブジェクトを選択します。 [インスペクター] パネルで [コンポーネントの追加] ボタンをクリックし、[オーディオソース] を検索して選択します。 後の方の手順で、このオーディオ ソースを使用して効果音を再生します。

    >[!NOTE]
    >Octa オブジェクトに box collider があることを確認します。

2. Near 対話 Touchable コンポーネントを追加します。 [インスペクター] パネルの [Add Component (コンポーネントの追加)] ボタンをクリックし、near インタラクション touchable を検索します。 選択してコンポーネントに追加します。

    >[!NOTE]
    >以前は、grabbable の近くに追加しました。 この相互作用 touchable の違いは、grabbable の相互作用は、オブジェクトをグラブして操作することを意図しています。 Touchable コンポーネントは、タッチするオブジェクトを対象としています。 操作を組み合わせるために両方のコンポーネントを一緒に使用することができます。

    ![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. ハンドインタラクションタッチスクリプトにを追加します。 前の手順と同じように、[コンポーネントの追加] をクリックして、追加するタッチ操作を検索します。

    スクリプトには次の3つのオプションがあることに注意してください。
    * タッチ完了時: オブジェクトをタッチして解放するとトリガーされます
    * タッチ開始時: オブジェクトがタッチされたときにトリガーします
    * タッチ更新時: ハンドがオブジェクトに接している間、定期的にトリガーします。

    この例では、[タッチによる開始] 設定を使用します。

    >[!NOTE]
    >このスクリプトは、このチュートリアルの冒頭でインポートした BaseModuleAssets Unity パッケージに含まれており、元の MRTK には含まれていません。

4. [タッチ開始時] オプションの [+] ボタンをクリックし、[Octa] オブジェクトを空のフィールドにドラッグします。

    ![mrlearning-base-ch4-4-step4](images/mrlearning-base-ch4-4-step4.png)

5. [関数がありません] というドロップダウンで、[AudioSource > PlayOneShot] を選択します。 以下のコンセプトを元に、このフィールドにオーディオ クリップを追加します。

    * MRTK には、オーディオ クリップの小さいリストがあります。 これらは、プロジェクトパネルで自由に調べることができます。 これらのファイルは、[アセット > MixedRealityToolkit > Standard Assets > Audio フォルダー] の下にあります。
    * この例では、MRTK_Gem オーディオクリップを使用します。
    * オーディオクリップを追加するには、目的のクリップを [プロジェクト] パネルから [PlayOneShot] フィールドにドラッグするだけです。

    ![mrlearning-base-ch4-4-step5](images/mrlearning-base-ch4-4-step5.png)

   これで、ユーザーがに到達し、Octa オブジェクトに触れると、オーディオトラック MRTK_Gem が再生されます。 また、ハンドインタラクションタッチスクリプトでは、オブジェクトの色も調整されます。

## <a name="congratulations"></a>結論

このチュートリアルでは、グリッドコレクション内の3D オブジェクトを整理する方法と、近くの操作 (追跡したハンドを使用した直接グラブ) と遠くの相互作用 (宝石を使用した、または光線を使用) を使用して、これらのオブジェクトを操作する方法について学習しました。 また、3D オブジェクトの周囲に境界ボックスを配置する方法と、境界ボックスでギズモを使用およびカスタマイズする方法についても学習しました。 最後に、オブジェクトにタッチしたときにイベントをトリガーする方法を学習しました。

[次のレッスン: 6. 詳細な入力オプションの調査](mrlearning-base-ch5.md)
