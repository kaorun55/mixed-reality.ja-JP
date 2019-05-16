---
title: MR Learning ベースのモジュールのユーザー インターフェイスでは、手 Tracking、および現実ツールキットの構成を混在
description: このコースでは、複合現実のアプリケーション内で Azure の顔認識機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 複合現実、unity、チュートリアル、hololens
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730952"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>MR Learning ベースのモジュールのユーザー インターフェイスでは、手 Tracking、および現実ツールキットの構成を混在

前のレッスンでは、HoloLens 2 の最初のアプリケーションを起動して、提供する、MRTK が持つ機能の一部を学習しました。 次のレッスンでは、作成し、UI テキスト パネルとボタンを編成および既定の操作 (タッチ) を使用して、各ボタンとやり取りする方法を学びます。 単純なアクションと、サイズ、サウンドを変更するなどの効果を追加し、オブジェクトの色の調査も行います。 このモジュールでは、空間メッシュの視覚化を無効にすることで始まる MRTK プロファイルを変更する方法の基本的な概念を紹介します。 

## <a name="objectives"></a>目標

* カスタマイズし、Mixed Reality Toolkit プロファイルを構成します。
* UI 要素とボタンを使用するホログラムと対話します。
* 基本的な追跡の手動入力との相互作用

## <a name="instructions"></a>手順

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>複合現実 Toolkit プロファイル (空間認識表示オプションを変更する) を構成する方法
カスタマイズおよび空間認識の表示オプションを調整することによって、Mixed Reality Toolkit の既定のプロファイルを構成する方法について説明しますが、このセクションでは次のようにメッシュです。 これらの同じ原則、設定や MRTK プロファイル内の値を調整するための手順に従います。

1. "BaseScene"階層から Mixed Reality ツールキット (MRTK) を選択します。 Inspector パネルは、「Mixed Reality Toolkit スクリプト」を検索し、次の図に示すように、「アクティブなプロファイル」を選択します。 ダブルクリックして開きます。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>注:既定では、MRTK プロファイルは編集できません。 これらは、既定のプロファイル テンプレートをコピーしてカスタマイズできます。 カスタマイズとプロファイルに複数のレイヤーがあるので、標準的な手法をコピーして、1 つまたは複数の設定を構成するときに、いくつかのプロファイルをカスタマイズします。
>
>MRTK プロファイルとそのアーキテクチャの詳細を検出するには、次を参照してください、 [MRTK ドキュメント](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)します。

2. それをカスタマイズする既定のプロファイルのコピーを作成します。 既定のプロファイルをコピーする、「コピーとカスタマイズ」をクリックします (イメージを参照してください) ボタンをクリックします。 これは、MRTK プロファイルのコピーを作成します。 MRTK プロファイルの独自のコピーではこのプロファイルで設定をカスタマイズする機能があるようになりました。 以降の手順で説明されている、このプロファイルでは、入れ子になった追加のプロファイルのコピー/カスタマイズ手順を繰り返しても必要になります。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. 空間認識メッシュの可視性を無効にします。 この場合、図のように「空間認識システム設定」を検索します。 「複製」の右側のボタンをクリックして、「空間認識システム プロファイル」に、既定のプロファイルをカスタマイズ可能なコピーに置き換えます。 ポップアップ ウィンドウが表示されている場合は、次の 2 つ目の図に示すように「複製」ボタンを押します。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. 既定の Mixed Reality 空間メッシュ オブザーバーのカスタムのコピーを作成します。 「Windows 混合現実空間メッシュ オブザーバー」追加オプションを表示する横の下矢印をクリックします。 これらのオプションでは、「既定の混合現実空間メッシュ オブザーバー」に表示されるがグレーで表示 (編集不可) 表示されます。 これを編集できるように、カスタマイズ可能なコピーを使用してこの既定のプロファイルを置き換える必要があります。 コピーを複製するには、(緑色の矢印でマークされている) の右側にボタンをクリックします。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. 次に、「オクルー ジョン」と表示オプションの設定を調整します。 これにより、空間メッシュは、非表示が、まだこれは、(遮蔽。) 空間のメッシュの背後にあるゲーム オブジェクトを非表示

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>注:空間マッピング メッシュが表示されていないときにまだ存在して、それと対話できます。 空間マッピング メッシュ (、見える壁の背後にあるホログラムなど) の背後にある任意のホログラムはオクルー ジョン設定によっては表示されません。

これで終了です。 だけ、MRTK プロファイルで設定を変更する方法を学習しました。 ご覧のとおり、それらを編集できるように、既定のプロファイルのコピーを作成する必要がある MRTK 設定を変更するためにします。 既定のプロファイル (これは編集できません) が常に、新しい設定でプロファイルを作成または既定のプロファイルを参照する場合に戻ります。 調整できる多数の設定があります。 MRTK プロファイルの設定への完全参照を MRTK のドキュメントを参照してください。 https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>手の追跡のジェスチャと対話型のボタン
このセクションでは、対話型のボタンを押すように追跡手の形を使用する方法を学びます。

1. [プロジェクト] フォルダーから、[アセット] を選択します。

2. 入力検索バーで、"pressablebutton"

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. "PressableButton"という名前のプレハブ (青のボックスで表される) を階層にドラッグします。 

   > 注:に関するメッセージを取得する場合は、この時点でインポートしてください「TMP Essentials をインポートする」。 TMP Essentials が既にプロジェクトの一部でない場合は、ボタンのテキストは記述できません。 それ以外の場合、TMP Essentials をインポートした後、この手順を繰り返す必要があります。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. (、ボタンの画像は、次の図とは異なる場合があります表示) の下の図のように、シーンに表示する (これは、BaseScene 階層になります)"PressableButton"ゲーム オブジェクトをダブルクリックします。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. インスペクター ウィンドウで、ボタンにプッシュされるときに応答するイベントを「イベントの追加」をクリックします。 オプションが表示されるは、ドロップダウン メニューを選択します。 "InteractableOnPressReciever。"を選択します。 これにより、追跡対象の手がボタンを押したときに押された状態のイベントに応答するボタンをクリックします。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. キューブをシーンに追加します。 階層領域を右クリックし、3 D オブジェクトを選択し、「キューブです」をクリックしてください ここで、キューブは、ディスプレイでなければなりません。 非常に大きく表示、ため調整座標 ("cube"は、階層領域で選択したまま) 中にサイズを小さくします。 スケールの値 x に設定 = 0.1、y = 0.1、z = 0.1 です。 Pressable のボタンの近くに配置して、シーン内のキューブを配置することを確認してがボタンに重複は許可されません。 次の図では、キューブの位置は x = 0、y = 0.2、および z = 1。 

   > 注:一般に、Unity で 1 ユニットは、物理世界で 1 m とほぼ同じです。 たとえば、オブジェクトがスケーリングされたオブジェクトの子の場合、この例外があります。
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. この手順では、色を変更するボタンが押されたときに、キューブを設定します。 "BaseScene"メニューで、PressableButton を選択します。 Inspector パネルで、"イベントの種類の選択 ボックスの下で「+」ボタンをクリックします。 次の図に示すようには、[ランタイムのみ] ボックスに"BaseScene"メニューから"cube"をドラッグします。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

「機能はありません。」ことを示すドロップダウン リストをクリックします。 "MeshRenderer"を選択し、"素材 material。"を選択します。 これによって、ボタンが押されたときに、マテリアルを変更できます。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

プロジェクト パネルとするように変更するマテリアルの検索に移動します。 "MRTK_Standard_Cyan"マテリアルを使用して、この例で、「シアン」(The MRTK を含む多くの資料や色から選択)、[プロジェクト] タブの検索バーに入力して検出します。"MeshRenderer.material。"の下のボックスに、マテリアルをドラッグします。 資産で見つかる MRTK 資料 > MixedRealityToolkit.SDK > StandardAssets > マテリアル。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

いるので、キューブが指定した material に基づいて色を変更、ボタンが押されたときに、イベントが設定されました。 この例では、キューブがシアンのカラーに変更されます。

8. 次に、リリース時に、ボタンに戻ってその既定の色ようにリリース アクションを設定することにします。 次の図に示すように、手順 7 (前の手順) が、この時点で、"OnPress"イベントではなく"OnRelease"イベントを繰り返します。

9.  プロジェクト パネルで、検索ボタンをクリックすると解放を既定値に、キューブの素材 (ここで選択した MRTK_Standard_LightGray)。マテリアルを"MeshRenderer.material"フィールドの下のボックスにドラッグします。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

これで、ボタンが押されたときに、新しい色に変わります (例: シアン) と、ボタンが離されたときに、指定した既定の色に変わります (薄い灰色など)。エディターで試すかをテストするには、HoloLens 2 への展開を画面の上部に「再生」ボタンがキーを押します。 エディターでのシミュレーション、読み取る手の形のシミュレーションを含む詳細について、 [MRTK のシミュレーションのドキュメント ページ](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)します。 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>MRTK の Grid オブジェクトのコレクションを使用してボタンのパネルを作成します。

このセクションでは、自動的に MRTK の GridObjectCollection ツールを使用して優れたユーザー インターフェイスに複数のボタンを配置する方法を学びます。

1. 5 個のボタンを設定するまでは、前のセクションからボタンを重複しています。 これを行ういくつかの方法はあります。
- ボタンを右クリックし「コピー」をクリックし、ボタンの下の下に移動し再び右クリックして「貼り付け」をクリックします。 
- ボタンを右クリックし、「重複しています。」をクリックします。 
- キーボード コマンドを使用するには、キューブとキーを押して"ctrl D"、キーボードをクリックします。

5 個の合計ボタン (次の図で赤の矢印を 5 を参照してください) になるまで、この手順を繰り返します。

![Mrlearning ベース Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. 空の親ゲーム オブジェクトの下のボタンをグループ化します。 グリッドのコレクションにあるボタンは、共通の親オブジェクトの下のボタンをグループ化する必要があります。 Hiearachy 内を右クリックし、「作成空」です。 これにより、新しい空のゲーム オブジェクトのすべてのボタンを配置するが作成されます。 "GameObject です"として表示されます。 右クリックし、"ButtonCollection"に変更します

![Mrlearning ベース Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. 新しいコレクションには、すべてのボタンを移動します。 これには、heirarch で 5 つのボタン オブジェクトのすべてを選択すると、次の図に示すように"ButtonCollection"のゲーム オブジェクトのすべてでドラッグしてください。 ヒント: は、ctrl キーを押しながら項目を選択するときに、複数の項目を選択します。

![Mrlearning ベース Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. MRTK の「グリッド オブジェクトのコレクション」のコンポーネントをボタンのコレクションに追加します。  これを行うには、"ButtonCollection"親オブジェクトを選択し、[inspector] パネルで、「コンポーネントの追加」ボタンをクリックします。 検索バーに「グリッドのオブジェクトのコレクション」を検索し、一覧に表示されるときに選択します。

![Mrlearning ベース Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

グリッド オブジェクトのコレクションのコンポーネントでは、ボタン、またはそのいずれかを整理できます。 便利な行、列、またはグリッド内のオブジェクトのセット。 これは、素晴らしいユーザー インターフェイスを作成する簡単な方法を提供する MRTK によって提供される構成要素のいずれかです。

5. グリッド オブジェクトのコレクションを構成します。 すべてのボタンの表面をユーザーに確実には、「型の向きを設定」を選択し、選択"親フォワード直面"を (図のようにします。)次に、ボタン間のスペースを設定するセルのサイズを変更します。 次の図に示すように、セルの幅とセルの高さの >=0.12 >=0.12 ユニット単位で開始します。 選択したオブジェクト/ボタン資産によって、これらの値を調整する必要があります。 「行」が 1 に設定されていることを確認します。 "コレクションの更新 をクリックし、シーンは、次の図のようになります。 


![Mrlearning ベース Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>注:オブジェクトの子または親オブジェクトの方向に応じて、今後のプロジェクトの設定が異なる向きを調整する必要があります。 セルの幅とセルの高さのフィールドは、コレクション内のオブジェクトのサイズによって異なる方法で定義する必要もあります。

### <a name="adding-text-into-your-scene"></a>シーンにテキストを追加します。

このセクションでは、追加して、複合現実エクスペリエンスを提供するテキストを編集する方法を学びます。 まだインストールしていない場合は、次の手順で、Unity で有効になっている TextMeshPro があるを確認してください[ここ](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)します。

1. "ButtonCollection"の親オブジェクトを選択し、コレクションを右クリックします。 ドロップダウン メニューで「3D オブジェクト」を展開し、"TextMeshPro-Text"を選択します。 次の図に示すように、ボタンのコレクションの下の TextMeshPro オブジェクトが表示されます。

![レッスン 2 の第 4 章 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![レッスン 2 の第 4 章 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. TextMeshPro コンポーネントのテキスト フィールドに (次に示すように、[inspector] パネルである)、"ボタン コレクション Text"に入力します。 テキストは、シーンに表示されますが、ボタンや不適切なサイズの背後にある非表示になります。

![レッスン 2 の第 4 章の手順 2](images/Lesson2_Chapter4_Step2.JPG)

3. テキストのサイズと配置の読みやすさを向上させるのには、フォントのサイズを変更する TextMeshPro コンポーネント内のフォント サイズ フィールドを調整します。 「Rect 変換」の位置と次の図に示すようにスケールを調整する必要があります。 このテキスト構成に使用される値の下のイメージを参照してくださいし、自由に、テキスト フィールドの配置とサイズをさらに向上させるために元の開始点として、これらの値を使用してください。

![レッスン 2 の第 4 章 Step3](images/Lesson2_Chapter4_Step3.JPG)
![レッスン 2 の第 4 章の手順 4](images/Lesson2_Chapter4_Step4.JPG)

5. ボタン オブジェクト上のテキスト値を変更するには、展開すると、"SeeItSayItLabel"オブジェクトに移動し、いずれかのボタンの横にある矢印をクリックし、"TextMeshPro、"に移動し、上記の手順」の説明に従って、ボタンにテキストを編集することができます。

![レッスン 2 の第 4 章の手順 5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>おめでとうございます
このレッスンでは、コピー、カスタマイズ、および MRTK プロファイル設定 (つまり、空間認識メッシュの可視性。) を構成する方法を説明トリガー イベントの追跡対象の手を使用して、HoloLens 2 にするためのボタンと対話する方法も学習しました。 最後に、Unity のテキストをメッシュ Pro を使用して、シンプルな UI インターフェイス MRTK の Grid オブジェクトのコレクションのコンポーネントを作成する方法を学習しました。

[次のレッスン:動的なコンテンツの配置とソルバー](mrlearning-base-ch3.md)

