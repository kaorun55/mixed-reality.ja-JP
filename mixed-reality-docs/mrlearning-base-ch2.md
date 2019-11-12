---
title: 入門チュートリアル-3. ユーザーインターフェイスを作成し、Mixed Reality Toolkit を構成する
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 0595010a0b443d88e3f208b785903e3f6cc99295
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926528"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. ユーザーインターフェイスを作成し、Mixed Reality Toolkit を構成する

前のレッスンでは、HoloLens 2 の最初のアプリケーションを開始することで、Mixed Reality Toolkit (MRTK) が提供する必要のある機能について説明しました。 次のレッスンでは、UI テキストパネルと共にボタンを作成および整理し、既定の対話機能 (タッチ) を使用して各ボタンを操作する方法について説明します。 また、オブジェクトのサイズ、音、色の変更など、単純なアクションや効果の追加も調査します。 このモジュールでは、[空間マッピング](spatial-mapping.md)メッシュの視覚化を無効にしてから、MRTK プロファイルの変更に関する基本的な概念を紹介します。

## <a name="objectives"></a>目標

* Mixed Reality ツールキット プロファイルをカスタマイズおよび構成する
* UI 要素とボタンを使用したホログラムとの対話
* 基本的な手の追跡の入力と操作

## <a name="instructions"></a>手順

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Mixed Reality Toolkit プロファイルを構成する方法 (空間認識表示オプションの変更)

このセクションでは、空間認識メッシュの表示オプションを調整して、既定の MRTK プロファイルをカスタマイズおよび構成する方法について説明します。 MRTK プロファイル内の設定または値を調整するには、次の同じ原則に従うことができます。

1. BaseScene 階層から Mixed-Reality Toolkit (MRTK) を選択します。 [インスペクター] パネルで、次の図に示すように、Mixed Reality Toolkit スクリプトを探し、アクティブなプロファイルを選択します。 それをダブルクリックして開きます。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step1.png)

    >[!NOTE]
    >既定では、MRTK プロファイルは編集できません。 これらは既定のプロファイルテンプレートで、コピーしてカスタマイズすることができます。 カスタマイズとプロファイルには、いくつかのレイヤーがあります。 そのため、1つまたは複数の設定を構成するときに、いくつかのプロファイルをコピーしてカスタマイズするのは標準的な方法です。
    >
    >MRTK プロファイルとそのアーキテクチャの詳細については、 [Mrtk のドキュメント](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>)を参照してください。

2. 既定のプロファイルのコピーを作成し、それをカスタマイズします。 **[コピー & カスタマイズ]** をクリックして開始します。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2a.png)

    これにより、[*複製プロファイル*] ポップアップウィンドウが開きます。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2b.png)

    **[複製]** をクリックして、MRTK プロファイルのコピーを作成します。 MRTK プロファイルの独自のコピーが取得できたので、このプロファイル内の任意の設定をカスタマイズできるようになりました。 また、後の手順で説明するように、このプロファイルの下に入れ子になっている追加のプロファイルについても、[コピーとカスタマイズ] ステップを繰り返す必要があります。

3. 空間認識メッシュの可視性を無効にします。 これを行うには、次の図に示すように、空間認識システムの設定を見つけます。 **[空間認識システムを有効にする]** オプションがオンになっていることを確認します。 空間認識システム プロファイルの右側にある **複製** ボタンをクリックして、既定のプロファイルをカスタマイズ可能なコピーに置き換えます。 次の2番目の図に示すように、表示されたポップアップウィンドウで、 **[複製]** ボタンをクリックします。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3a.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3b.png)

4. 既定の Mixed Reality 空間メッシュ オブザーバーのカスタム コピーを作成します。 [Windows Mixed Reality 空間メッシュオブザーバー] の横にある下矢印をクリックすると、追加のオプションが表示されます。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4a.png)

    これらのオプションでは、既定の Mixed Reality 空間メッシュオブザーバー (編集不可) がグレーで表示されます。 この既定のプロファイルをカスタマイズ可能なコピーに置き換えて編集できるようにする必要があります。 前に行ったように、 **[複製]** ボタンをクリックし、表示されたポップアップウィンドウで、下の2番目の図に示すように、 **[複製]** ボタンをクリックします。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4b.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4c.png)

5. 次に、表示オプションの設定を [オクルージョン] が表示されるように調整します。 これにより、空間マッピングメッシュは非表示になりますが、空間マッピングメッシュの背後にあるゲームオブジェクトは、遮蔽とも呼ばれます。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step5.png)

    >[!NOTE]
    >注: 空間マッピングメッシュは表示されていませんが、まだ存在しているので、操作できます。 空間マッピングメッシュの背後にあるホログラム (表示されているウォールの背後にあるホログラムなど) は、遮蔽の設定により表示されません。

これで終了です。 ここまで、MRTK プロファイル内の設定を変更する方法を学習しました。 見てわかるように、MRTK の設定を変更するには、既定のプロファイルのコピーを作成して編集できるようにする必要があります。 新しい設定でプロファイルを作成する場合、または既定のプロファイルを参照する場合は、既定のプロファイル (編集不可) が常に表示されます。 調整できる設定には多くのものがあります。 MRTK プロファイル設定の完全な参照については、MRTK のドキュメントを参照してください: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>手の追跡のジェスチャと操作可能なボタン

このセクションでは、ハンドトラッキングを使用して pressable ボタンを押す方法について説明します。

1. Projects フォルダーから Assets を選択します。

2. 検索バーに「PressableButtonHoloLens2」と入力します。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step2.png)

3. "PressableButtonHoloLens2" という名前の prefab (青いボックスで表されます) を階層にドラッグし、position 値を x = 0、y = 0 および z = 0.2 に設定して、ボタンがカメラの前にあるように設定します。 (カメラは元の位置に配置されています)。

    >[!NOTE]
    >"TMP Essentials をインポートしています" というメッセージが表示された場合は、この時点でインポートします。 TMP Essentials がプロジェクトの一部ではない場合は、TMP Essentials をインポートした後にこの手順を繰り返す必要がある場合があります。それ以外の場合は、ボタンテキストが表示されないことがあります。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step3.png)

4. シーンにキューブを追加します。 [階層] 領域を右クリックし、3D オブジェクトを選択してから、[キューブ] をクリックします。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6a.png)

    ここで、キューブが表示されます。 非常に大きいように見えます。 サイズを縮小するには、[階層] 領域で [キューブ] を選択した状態で、座標を調整します。 小数点以下桁数の値を x = 0.02、y = 0.02、z = 0.02 に設定します。 キューブは、ボタンの近くのシーンに配置してください。ただし、重なっていないようにしてください。 次の図では、キューブの位置は x = 0、y = 0.4、z = 0.2 です。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6b.png)

    >[!NOTE]
    >一般に、Unity の 1 ユニットは現実の世界のほぼ 1 m に相当します。 これには、あるオブジェクトがスケーリングされたオブジェクトの子である場合などの例外があります。

5. PressableButtonHoloLens2 game オブジェクトを選択した状態で、インスペクターの下方向へスクロールして、対話型 (スクリプト) コンポーネントのイベントセクションを探します。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step4.png)

6. プッシュ時に応答するイベントをボタンに与えるように、既存のイベントを変更します。 ご覧のように、イベントレシーバーの種類は InteractableOnPressReceiver に設定されています。 これにより、このボタンは、追跡対象の手がボタンを押したら押されたイベントに応答できるようになります。 この時点で、相互作用フィルターも Near と Far に変更する必要があります。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step5.png)

7. この手順では、ボタンが押されたら色を変更するようにキューブを設定します。 BaseScene 階層で PressableButtonHoloLens2 を選択し、次の図に示すように、[キューブ] ゲームオブジェクトを [BaseScene] 階層から [ランタイムのみ] フィールドにドラッグします。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7a.png)

    [関数なし] というドロップダウンリストをクリックします。 [MeshRenderer] を選択し、[素材マテリアル] を選択します。 これにより、ボタンが押されたときに素材を変更できます。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7b.png)

    [空の素材] フィールドの横にある円をクリックして、[素材の選択] ポップアップを開きます。 MRTK には、選択する多くの素材と色が含まれています。 この例では、ポップアップ検索バーに「MRTK_Standard」と入力することによって検出された素材 MRTK_Standard_Cyan を使用します。 素材フィールドを設定するには、MRTK_Standard_Cyan マテリアルを選択します。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7c.png)

    これで、このイベントは、ボタンが押されたら、指定された素材に基づいてキューブが色を変更するように設定されました。 この例では、キューブはシアン色に変更されます。

8. 次に、ボタンが放されたら、ボタンが既定の色に戻るように、ボタンを放すアクションを設定します。 上記の手順 7. を繰り返します。 ここでは、次の図に示すように、Onrelease MRTK_Standard_LightGray マテリアルではなく OnRelease イベントを使用します。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step8.png)

    これで、ボタンが押されたときに、新しい色シアンに変わります。 ボタンが離されると、指定した既定の色 (淡い灰色など) に戻ります。画面の上部にある [再生] ボタンをクリックして、エディターで試してみるか、HoloLens 2 に展開してテストします。 ハンドシミュレーションなど、エディター内のシミュレーションの詳細については、 [Mrtk のシミュレーションに関するドキュメントのページ](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)を参照してください。

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>MRTK のグリッド オブジェクト コレクションを使用したボタンのパネルの作成

このセクションでは、MRTK の GridObjectCollection ツールを使用して、複数のボタンを適切なユーザーインターフェイスに自動的に配置する方法について説明します。

1. 5つのボタンが表示されるまで、前のセクションのボタンを複製します。 これを行うには、ボタンを右クリックし、[コピー] をクリックします。 次に、ボタンの下に移動し、もう一度右クリックして、[貼り付け] をクリックします。
    -ボタンを右クリックし、[複製] をクリックします。
    -キューブをクリックし、キーボードの Ctrl D キーを押して、キーボードコマンドを使用します。

    5つのボタンが表示されるまで、この手順を繰り返します。下の画像の5つの赤い矢印をご覧ください。

    ![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. ボタンを空の親ゲーム オブジェクトの下にグループ化します。 グリッドコレクション内のボタンを使用するには、共通の親オブジェクトの下にボタンをグループ化する必要があります。 Hiハイキング achy を右クリックし、[空の作成] をクリックします。 これにより、すべてのボタンを配置するための新しい空のゲーム オブジェクトが作成されます。 これは、"説明" オブジェクトとして表示されます。 右クリックし、ButtonCollection という名前を変更します。

    ![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. すべてのボタンを新しいコレクションに移動します。 これを行うには、階層内の5つのボタンオブジェクトをすべて選択し、次の図に示すように、[ButtonCollection game] オブジェクトの下にすべてをドラッグします。 ヒント: 複数の項目を選択するには、Ctrl キーを押しながら項目を選択します。

    ![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. MRTK の Grid オブジェクトコレクションコンポーネントをボタンコレクションに追加します。 これを行うには、ButtonCollection 親オブジェクトを選択します。 [インスペクター] パネルで、[コンポーネントの追加] ボタンをクリックします。 検索バーで Grid オブジェクトコレクションを検索し、一覧に表示されたらそれを選択します。

    ![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3-step4.png)

    Grid オブジェクトコレクションコンポーネントを使用すると、適切な行、列、またはグリッド内のボタンまたはオブジェクトのセットを整理できます。 これは、MRTK によって提供される構成要素の1つであり、魅力的ユーザーインターフェイスをすばやく簡単に作成できます。

5. グリッド オブジェクト コレクションを構成します。 すべてのボタンがユーザーに面していることを確認するには、[回転の種類] を選択します。 次の図に示すように、[親を前方に移動] を選択します。 次に、ボタンの間のスペースを設定するためにセル サイズを変更します。 次の図に示すように、セルの幅とセルの高さを0.05 単位で0.05 単位で開始します。 Distance が0に設定され、Rows が1に設定されていることを確認します。 [コレクションの更新] をクリックします。 シーンは次の図のようになります。

    ![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3-step5.png)

    >[!NOTE]
    >子オブジェクトまたは親オブジェクトの向きによっては、将来のプロジェクトで、向きの設定を異なった方法で調整することが必要になる可能性があります。 また、コレクション内のオブジェクトのサイズによっては、[セルの幅] や [セルの高さ] のフィールドも異なった方法で定義することが必要になる可能性があります。

### <a name="adding-text-into-your-scene"></a>シーンへのテキストの追加

このセクションでは、テキストを Mixed Reality エクスペリエンスに追加したり編集したりする方法を学習します。 まだ行っていない場合は、[ここ](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)にある手順に従って、Unity で TextMeshPro を有効にするようにしてください。

1. ButtonCollection 親オブジェクトを選択し、コレクションを右クリックします。 ドロップダウンメニューの [3D オブジェクト] を展開します。 次に、[TextMeshPro] を選択します。 次の図に示すように、ボタンコレクションの下に TextMeshPro オブジェクトが表示されます。

    ![レッスン 2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG) ![レッスン 2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. テキストのサイズと位置を読みやすくするために、TextMeshPro コンポーネントの [フォントサイズ] フィールドを調整してフォントのサイズを変更します。 また、次の図に示すように、Rect の位置とスケールを調整する必要があります。 テキストの構成に使用される値については、以下の画像を参照してください。 テキストフィールドのサイズと配置をさらに向上させるための出発点として、これらの値を自由に使用してください。

    ![レッスン 2 Chapter4 手順3](images/mrlearning-base-ch2-4-step3.png)

3. 次の図に示すように、[インスペクター] パネルの TextMeshPro コンポーネントの [テキスト] フィールドに「Button Collection Text」と入力し、[Alignment] プロパティを [Center] と [Top] に調整します。

    ![レッスン 2 Chapter4 手順4](images/mrlearning-base-ch2-4-step4.png)

4. ボタンオブジェクトのテキスト値を変更するには、任意のボタンの横にある矢印をクリックして展開し、[参照] をクリックします。 上の手順で説明したように、ボタンにテキストを編集できる TextMeshPro に移動します。

    ![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a>結論

このレッスンでは、MRTK プロファイル設定をコピー、カスタマイズ、構成する方法 (つまり、空間認識メッシュの可視性) について学習しました。また、HoloLens 2 で追跡されたユーザーを使用してイベントをトリガーするボタンを操作する方法についても学習しました。 最後に、Unity のテキストメッシュ Pro と MRTK の Grid オブジェクトコレクションコンポーネントを使用して、簡単な UI インターフェイスを作成する方法を学習しました。

[次のレッスン: 4. 動的なコンテンツを配置し、ソルバーを使用する](mrlearning-base-ch3.md)
