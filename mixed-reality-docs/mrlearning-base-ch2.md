---
title: 入門チュートリアル-3. ユーザーインターフェイスを作成し、Mixed Reality Toolkit を構成する
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 925ab825c2716a847726ac763dc6800914d87c6b
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702036"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3.ユーザーインターフェイスを作成し、Mixed Reality Toolkit を構成する 

前のレッスンでは、HoloLens 2 の最初のアプリケーションを開始することで、Mixed Reality Toolkit (MRTK) が提供する必要のある機能について説明しました。 次のレッスンでは、UI テキストパネルと共にボタンを作成および整理し、既定の対話機能 (タッチ) を使用して各ボタンを操作する方法について説明します。 また、オブジェクトのサイズ、音、色の変更など、単純なアクションや効果の追加も調査します。 このモジュールでは、空間メッシュの視覚化を無効にしてから、MRTK プロファイルの変更に関する基本的な概念を紹介します。 

## <a name="objectives"></a>目的

* Mixed Reality ツールキット プロファイルをカスタマイズおよび構成する
* UI 要素とボタンを使用したホログラムとの対話
* 基本的な手の追跡の入力と操作

## <a name="instructions"></a>手順

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Mixed Reality ツールキット プロファイルを構成する (空間認識の表示オプションを変更する) 方法
このセクションでは、空間認識メッシュの表示オプションを調整して、既定の MRTK プロファイルをカスタマイズおよび構成する方法について説明します。 MRTK プロファイル内の設定または値を調整するには、次の同じ原則に従うことができます。

1. BaseScene 階層から Mixed-Reality Toolkit (MRTK) を選択します。 [インスペクター] パネルで、次の図に示すように、Mixed Reality Toolkit スクリプトを探し、アクティブなプロファイルを選択します。 それをダブルクリックして開きます。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>注:既定では、MRTK プロファイルは編集できません。 これらは既定のプロファイルテンプレートで、コピーしてカスタマイズすることができます。 カスタマイズとプロファイルには、いくつかのレイヤーがあります。 そのため、1つまたは複数の設定を構成するときに、いくつかのプロファイルをコピーしてカスタマイズするのは標準的な方法です。
>
>MRTK プロファイルとそのアーキテクチャの詳細については、 [Mrtk のドキュメント](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)を参照してください。

2. 既定のプロファイルのコピーを作成し、それをカスタマイズします。 既定のプロファイルをコピーするには、[コピー & カスタマイズ] をクリックします (イメージを参照)。 これにより、MRTK プロファイルのコピーが作成されます。 MRTK プロファイルの独自のコピーが取得できたので、このプロファイル内の任意の設定をカスタマイズできるようになりました。 また、後の手順で説明するように、このプロファイルの下に入れ子になっている追加のプロファイルについても、[コピーとカスタマイズ] ステップを繰り返す必要があります。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. 空間認識メッシュの可視性を無効にします。 これを行うには、イメージに示されているように、空間認識システム設定を見つけます。 [空間認識システム] プロファイルの右側にある [複製] ボタンをクリックして、既定のプロファイルをカスタマイズ可能なコピーに置き換えます。 ポップアップウィンドウが表示された場合は、次の2番目の図に示すように、[複製] ボタンをクリックします。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. 既定の Mixed Reality 空間メッシュ オブザーバーのカスタム コピーを作成します。 [Windows Mixed Reality 空間メッシュオブザーバー] の横にある下矢印をクリックすると、追加のオプションが表示されます。 これらのオプションでは、既定の Mixed Reality 空間メッシュオブザーバー (編集不可) がグレーで表示されます。 この既定のプロファイルをカスタマイズ可能なコピーに置き換えて編集できるようにする必要があります。 右側のボタン (緑色の矢印でマークされています) をクリックして、コピーを複製します。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. 次に、表示オプションの設定を [オクルージョン] が表示されるように調整します。 これにより、空間メッシュは非表示になりますが、空間メッシュの背後にあるゲームオブジェクトは、遮蔽とも呼ばれます。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>注:空間マッピング メッシュは表示されていないときも引き続き存在し、ユーザーから操作できます。 空間マッピングメッシュの背後にあるホログラム (表示されているウォールの背後にあるホログラムなど) は、遮蔽の設定により表示されません。

おめでとうございます! ここまで、MRTK プロファイル内の設定を変更する方法を学習しました。 見てわかるように、MRTK の設定を変更するには、既定のプロファイルのコピーを作成して編集できるようにする必要があります。 新しい設定でプロファイルを作成する場合、または既定のプロファイルを参照する場合は、既定のプロファイル (編集不可) が常に表示されます。 調整できる設定には多くのものがあります。 MRTK プロファイルの設定の完全なリファレンスについては、MRTK のドキュメント (https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html ) を参照してください。

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>手の追跡のジェスチャと操作可能なボタン
このセクションでは、ハンドトラッキングを使用して pressable ボタンを押す方法について説明します。

1. Projects フォルダーから Assets を選択します。

2. 検索バーに「pressablebutton」と入力します。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. [PressableButton] という名前のプレハブ (青色のボックスで表されています) を階層にドラッグします。 

   > 注:"TMP Essentials をインポートしています" というメッセージが表示された場合は、この時点でインポートします。 TMP Essentials がプロジェクトの一部ではない場合は、TMP Essentials をインポートした後にこの手順を繰り返す必要がある場合があります。それ以外の場合は、ボタンテキストが表示されないことがあります。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. 次の図に示すように、[PressableButton] ゲームオブジェクトをダブルクリックして、BaseScene 階層に表示されるようにします。 ボタンのグラフィックスは、次の画像とは異なる場合があります。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. [インスペクター] パネルで、[イベントの追加] をクリックして、プッシュ時に応答するイベントをボタンに与えます。 表示されるオプションで、ドロップダウンメニューを選択し、[InteractableOnPressReciever] を選択します。 これにより、このボタンは、追跡対象の手がボタンを押したら押されたイベントに応答できるようになります。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. シーンにキューブを追加します。 [階層] 領域を右クリックし、3D オブジェクトを選択してから、[キューブ] をクリックします。 ここで、キューブが表示されます。 非常に大きいように見えます。 サイズを縮小するには、[階層] 領域で [キューブ] を選択した状態で、座標を調整します。 スケール値を x = 0.1、y = 0.1、z = 0.1 に設定します。 キューブをシーン内に配置して、押しボタンの近くだが、ボタンと重ならない位置に置くようにしてください。 次の図では、キューブの位置は x = 0、y = 0.2、z = 1 です。 

   > 注:一般に、Unity の 1 ユニットは現実の世界のほぼ 1 m に相当します。 これには、あるオブジェクトがスケーリングされたオブジェクトの子である場合などの例外があります。
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. この手順では、ボタンが押されたら色を変更するようにキューブを設定します。 BaseScene メニューの [PressableButton] を選択します。 [インスペクター] パネルの [イベントの種類の選択] ボックスで、[+] ボタンをクリックします。 次の図に示すように、[BaseScene] メニューから [ランタイムのみ] ボックスにキューブをドラッグします。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

[関数なし] というドロップダウンリストをクリックします。 [MeshRenderer] を選択し、[素材マテリアル] を選択します。 これにより、ボタンが押されたときに素材を変更できます。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

[プロジェクト] パネルに移動し、変更する素材を検索します。 この例では、MRTK_Standard_Cyan というマテリアルを使用します。この例では、[プロジェクト] タブの検索バーに「水色」と入力します。 (MRTK には、選択する多くの素材と色が含まれています)。素材を MeshRenderer の下のボックスにドラッグします。 MRTK の素材は、[アセット]>[MixedRealityToolkit.SDK]>[StandardAssets]>[素材] で見つけることができます。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

これで、このイベントは、ボタンが押されたら、指定された素材に基づいてキューブが色を変更するように設定されました。 この例では、キューブはシアン色に変更されます。

8. 次に、ボタンが放されたら、ボタンが既定の色に戻るように、ボタンを放すアクションを設定します。 上記の手順 7. を繰り返します。 ここでは、次の図に示すように、Onrelease イベントではなく OnRelease イベントを使用します。

9.  [プロジェクト] パネルで、ボタンのリリース時に既定で使用するキューブの素材を検索します。 この例では、[MRTK_Standard_LightGray] を選択しました。 素材を MeshRenderer フィールドの下のボックスにドラッグします。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

これで、ボタンが押されたときに、新しい色シアンに変わります。 ボタンが離されると、指定した既定の色 (淡い灰色など) に戻ります。画面の上部にある [再生] ボタンをクリックして、エディターで試してみるか、HoloLens 2 に展開してテストします。 ハンドシミュレーションなど、エディター内のシミュレーションの詳細については、 [Mrtk のシミュレーションに関するドキュメントのページ](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)を参照してください。 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>MRTK のグリッド オブジェクト コレクションを使用したボタンのパネルの作成

このセクションでは、MRTK の GridObjectCollection ツールを使用して、複数のボタンを適切なユーザーインターフェイスに自動的に配置する方法について説明します。

1. 5つのボタンが表示されるまで、前のセクションのボタンを複製します。 これにはいくつかの方法があります。
- ボタンを右クリックし、[コピー] をクリックします。 次に、ボタンの下に移動し、もう一度右クリックして、[貼り付け] をクリックします。 
- ボタンを右クリックし、[複製] をクリックします。 
- キューブをクリックし、キーボードの Ctrl D キーを押して、キーボードコマンドを使用します。

5つのボタンが表示されるまで、この手順を繰り返します。下の画像の5つの赤い矢印をご覧ください。

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. ボタンを空の親ゲーム オブジェクトの下にグループ化します。 グリッドコレクション内のボタンを使用するには、共通の親オブジェクトの下にボタンをグループ化する必要があります。 Hiハイキング achy を右クリックし、[空の作成] をクリックします。 これにより、すべてのボタンを配置するための新しい空のゲーム オブジェクトが作成されます。 これは、"説明" オブジェクトとして表示されます。 右クリックし、ButtonCollection という名前を変更します。

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. すべてのボタンを新しいコレクションに移動します。 これを行うには、階層内の5つのボタンオブジェクトをすべて選択し、次の図に示すように、[ButtonCollection game] オブジェクトの下にすべてをドラッグします。 ヒント: 複数の項目を選択するには、Ctrl キーを押しながら項目を選択します。

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. MRTK の Grid オブジェクトコレクションコンポーネントをボタンコレクションに追加します。 これを行うには、ButtonCollection 親オブジェクトを選択します。 [インスペクター] パネルで、[コンポーネントの追加] ボタンをクリックします。 検索バーで Grid オブジェクトコレクションを検索し、一覧に表示されたらそれを選択します。

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

Grid オブジェクトコレクションコンポーネントを使用すると、適切な行、列、またはグリッド内のボタンまたはオブジェクトのセットを整理できます。 これは、MRTK によって提供される構成要素の1つであり、魅力的ユーザーインターフェイスをすばやく簡単に作成できます。

5. グリッド オブジェクト コレクションを構成します。 すべてのボタンがユーザーに面していることを確認するには、[回転の種類] を選択します。 次の図に示すように、[親を前方に移動] を選択します。 次に、ボタンの間のスペースを設定するためにセル サイズを変更します。 次の図に示すように、セルの幅とセルの高さを0.12 単位で0.12 単位で開始します。 選択されたオブジェクトとボタンアセットによっては、これらの値の調整が必要になる場合があります。 行が1に設定されていることを確認します。 [コレクションの更新] をクリックします。 シーンは次の図のようになります。 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>注:子オブジェクトまたは親オブジェクトの向きによっては、将来のプロジェクトで、向きの設定を異なった方法で調整することが必要になる可能性があります。 また、コレクション内のオブジェクトのサイズによっては、[セルの幅] や [セルの高さ] のフィールドも異なった方法で定義することが必要になる可能性があります。

### <a name="adding-text-into-your-scene"></a>シーンへのテキストの追加

このセクションでは、テキストを Mixed Reality エクスペリエンスに追加したり編集したりする方法を学習します。 まだ行っていない場合は、[ここ](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)にある手順に従って、Unity で TextMeshPro を有効にするようにしてください。

1. ButtonCollection 親オブジェクトを選択し、コレクションを右クリックします。 ドロップダウンメニューの [3D オブジェクト] を展開します。 次に、[TextMeshPro] を選択します。 次の図に示すように、ボタンコレクションの下に TextMeshPro オブジェクトが表示されます。

![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. テキストのサイズと位置を読みやすくするために、TextMeshPro コンポーネントの [フォントサイズ] フィールドを調整してフォントのサイズを変更します。 また、次の図に示すように、Rect の位置とスケールを調整する必要があります。 テキストの構成に使用される値については、以下の画像を参照してください。 テキストフィールドのサイズと配置をさらに向上させるための出発点として、これらの値を自由に使用してください。

![レッスン 2 Chapter4 手順3](images/Lesson2_Chapter4_Step3.JPG)

3. 次に示すように、[インスペクター] パネルの TextMeshPro コンポーネントのテキストフィールドに入力します。 ボタンコレクションのテキストを入力します。 テキストはシーンに表示されますが、ボタンの背後に表示されないか、またはサイズが正しくありません。

![レッスン 2 Chapter4 の](images/Lesson2_Chapter4_Step2.JPG)
ステップ![レッスン 2 Chapter4 手順4](images/Lesson2_Chapter4_Step4.JPG)

4. ボタンオブジェクトのテキスト値を変更するには、任意のボタンの横にある矢印をクリックして展開し、[参照] をクリックします。 上の手順で説明したように、ボタンにテキストを編集できる TextMeshPro に移動します。

![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a>結論
このレッスンでは、MRTK プロファイルの設定 (つまり、空間認識メッシュの可視性) をコピー、カスタマイズ、および構成する方法を学習しました。また、HoloLens 2 で追跡対象の手を使用して、イベントをトリガーするためにボタンを操作する方法も学習しました。 最後に、Unity の Text Mesh Pro (MRTK の [グリッド オブジェクト コレクション] コンポーネント) を使用して単純な UI インターフェイスを作成する方法を学習しました。

[次のレッスン:4。動的なコンテンツの配置とソルバーの使用](mrlearning-base-ch3.md)

