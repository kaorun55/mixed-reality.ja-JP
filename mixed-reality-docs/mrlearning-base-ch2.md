---
title: 入門チュートリアル-3. ユーザーインターフェイスを作成し、Mixed Reality Toolkit を構成する
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: f1d042150d1c81940e672b174c6c02ac71e05883
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554883"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. ユーザーインターフェイスを作成し、Mixed Reality Toolkit を構成する
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

前のチュートリアルでは、HoloLens 2 の最初のアプリケーションを開始することで、Mixed Reality Toolkit (MRTK) が提供する必要のある機能の一部について学習しました。 このチュートリアルでは、UI テキストパネルと共にボタンを作成および整理し、既定の対話機能 (タッチ) を使用して各ボタンを操作する方法について説明します。 また、オブジェクトのサイズ、音、色の変更など、単純なアクションや効果の追加も調査します。 このモジュールでは、[空間マッピング](spatial-mapping.md)メッシュの視覚化を無効にしてから、MRTK プロファイルの変更に関する基本的な概念を紹介します。

## <a name="objectives"></a>目標

* Mixed Reality ツールキット プロファイルをカスタマイズおよび構成する
* UI 要素とボタンを使用したホログラムとの対話
* 基本的な手の追跡の入力と操作

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Mixed Reality Toolkit プロファイルを構成する方法 (空間認識表示オプションの変更)
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

このセクションでは、既定の MRTK プロファイルをカスタマイズして構成する方法について説明します。

この特定の例では、空間メッシュオブザーバーの設定を変更して、空間認識メッシュを非表示にする方法を示します。 ただし、これらの同じ原則に従って、MRTK プロファイルの設定または値をカスタマイズすることもできます。

空間認識メッシュを非表示にするには、主に次の手順を実行します。

1. 既定の構成プロファイルの複製
2. 空間認識システムを有効にする
3. 既定の空間認識システムプロファイルを複製する
4. 既定の空間認識メッシュオブザーバープロファイルを複製します
5. 空間認識メッシュの可視性を変更する

> [!NOTE]
> 既定では、MRTK プロファイルは編集できません。 これらは、編集する前に複製する必要がある既定のプロファイルテンプレートです。 プロファイルには、入れ子になったレイヤーがいくつかあります。 そのため、1つまたは複数の設定を構成するときに、複数のプロファイルを複製して編集するのが一般的です。

### <a name="1-clone-the-default-configuration-profile"></a>1. 既定の構成プロファイルを複製します。

> [!NOTE]
> 構成プロファイルは最上位レベルのプロファイルです。 そのため、他のプロファイルを編集できるようにするには、まず、構成プロファイルを複製する必要があります。

[階層] ウィンドウで**MixedRealityToolkit**オブジェクトを選択し、[インスペクター] ウィンドウで Mixed Reality Toolkit**構成プロファイル**を**DefaultHoloLens2ConfigurationProfile**に変更します。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

**MixedRealityToolkit**オブジェクトを選択した状態で、インスペクター ウィンドウの **カスタマイズのコピー &** をクリックして、プロファイルの複製 ウィンドウを開きます。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

複製プロファイル ウィンドウで、**複製** ボタンをクリックして、 **DefaultHololens2ConfigurationProfile**の編集可能なコピーを作成します。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

新しく作成された構成プロファイルが、シーンの構成プロファイルとして割り当てられました。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

Unity メニューで、[**ファイル** > **保存**] を選択してシーンを保存します。

> [!TIP]
> チュートリアル全体で作業内容を保存してください。

### <a name="2-enable-the-spatial-awareness-system"></a>2. 空間認識システムを有効にする

階層 ウィンドウで**MixedRealityToolkit**オブジェクトを選択した状態で、インスペクター ウィンドウで **空間認識** タブを選択し、**空間認識システムを有効にする** チェックボックスをオンにします。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. 既定の空間認識システムプロファイルを複製する

**空間認識** タブで、**複製** ボタンをクリックして プロファイルの複製 ウィンドウを開きます。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

複製プロファイル ウィンドウで、**複製** ボタンをクリックして、 **DefaultMixedRealitySpatialAwarenessSystemProfile**の編集可能なコピーを作成します。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

新しく作成された空間認識システムプロファイルが、構成プロファイルに自動的に割り当てられるようになりました。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. 既定の空間認識メッシュオブザーバープロファイルを複製する

**空間認識** タブを選択したまま、**Windows Mixed Reality 空間メッシュオブザーバー** セクションを展開し、**複製** ボタンをクリックして プロファイルの複製 ウィンドウを開きます。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

複製プロファイル ウィンドウで、**複製** ボタンをクリックして、 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**の編集可能なコピーを作成します。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

新しく作成された空間認識メッシュオブザーバーのプロファイルが、空間認識システムプロファイルに自動的に割り当てられるようになりました。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. 空間認識メッシュの可視性を変更する

**空間メッシュのオブザーバーの設定**で、**表示オプション**を **[オクルージョン]** に変更します。これにより、まだ機能している間に空間マッピングメッシュが非表示になります。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> 空間マッピングメッシュは見えませんが、まだ存在し、機能しています。 たとえば、物理的な壁の背後にあるホログラムなど、空間マッピングメッシュの背後にあるホログラムは、表示されません。

ここまで、MRTK プロファイル内の設定を変更する方法を学習しました。 ご覧のとおり、MRTK の設定をカスタマイズするには、最初に既定のプロファイルのコピーを作成する必要があります。 既定のプロファイルは編集できないため、既定の設定に戻す場合は、常に参照として使用されます。 MRTK プロファイルとそのアーキテクチャの詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[Mixed Reality Toolkit プロファイル構成ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)を参照してください。

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>ハンドトラッキングジェスチャと対話型ボタン

このセクションでは、ハンドトラッキングを使用してボタンをクリックし、イベントをトリガーして、ボタンが押されたときにアクションを発生させる方法について説明します。

この特定の例では、ボタンが押されたときにキューブの色を変更し、ボタンが離されたときに元の色に戻るように変更する方法を示します。 ただし、同じ原則に従って他のイベントを作成することもできます。

キューブの色を変更するには、次の手順を実行します。

1. シーンに pressable button prefab を追加する
2. シーンへのキューブの追加
3. InteractableOnPressReceiver イベントの種類を構成する
4. On Press イベントを受け取るようにキューブを構成する
5. On Press イベントによってトリガーされるアクションを定義します
6. On Release イベントを受け取るようにキューブを構成する
7. On Release イベントによってトリガーされるアクションを定義します
8. エディター内シミュレーションを使用してボタンをテストする

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1. シーンに pressable button prefab を追加する

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a>は Unity アセットとして保存されている構成済みのユーザーオブジェクトであり、プロジェクト全体で再利用できます。

[**プロジェクト] ウィンドウ**で、 **PressableButtonHoloLens2**を検索して、この例で使用する prefab を探します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

**検索**結果で**PressableButtonHoloLens2** prefab を選択し、それを **[階層]** ウィンドウに**ドラッグ**してシーンに追加します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> 次の図に示すようにシーンを表示するには、[階層] ウィンドウで PressableButtonHoloLens2 オブジェクトをダブルクリックしてフォーカスを設定し、[シーン] ウィンドウの右上隅にある<a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">シーンの Gizmo</a>を使用して、前方 Z 軸に沿って表示角度を調整します。

**PressableButtonHoloLens2**オブジェクトを選択したまま、 **[インスペクター]** ウィンドウで次のようにします。

* カメラの前に配置されるように変換**位置**を変更する (例: x = 0、y = 0、z = 0.5)

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> 一般に、Unity の1つの位置単位は、物理的な世界では1メートルとほぼ同じです。 ただし、オブジェクトがスケーリングされたオブジェクトの子である場合などに、この例外が発生します。

### <a name="2-add-a-cube-to-the-scene"></a>2. シーンにキューブを追加する

[階層] ウィンドウ内の空の場所を右クリックし、[ **3D オブジェクト** > **キューブ**] を選択して、キューブをシーンに追加します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

**キューブ**オブジェクトを選択した状態で、 **[インスペクター]** ウィンドウで次のようにします。

* Pressable ボタンの近くに配置されるように変換**位置**を変更します。ただし、x = 0、y = 0.04、z = 0.5 など、重複しないようにします。
* 変換**スケール**を適切なサイズに変更します (たとえば、x = 0.02、y = 0.02、z = 0.02)。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3. InteractableOnPressReceiver イベントの種類を構成する

[階層] ウィンドウで、 **PressableButtonHoloLens2**オブジェクトを選択します。次に、 **[インスペクター]** ウィンドウ**ハンバーガーメニュー**で、 **[すべてのコンポーネントを折りたたむ]** を選択して、このオブジェクトのすべてのコンポーネントの概要を取得します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

**対話型 (スクリプト)** コンポーネントを展開し、[**イベント** > **レシーバー** ] セクションを探して展開します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

**[イベントの追加]** ボタンをクリックして、イベントレシーバーの種類が**Interactableonpressreceiver**の新しいイベントレシーバーを作成します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> InteractableOnPressReceiver という名前のイベントレシーバーの種類を使用すると、追跡したハンドがボタンを押したときに、ボタンが押されたイベントに応答できるようになります。

新しく作成されたイベントレシーバーについて、**相互作用フィルター**を**Near と Far**に変更します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4. On Press イベントを受け取るようにキューブを構成する

[階層] ウィンドウで、 **On press** () イベントの **[イベントのプロパティ]** オブジェクトフィールドに**キューブ**をクリックして**ドラッグ**します。これにより、on press () イベントの受信者としてキューブが割り当てられます。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5. On Press イベントによってトリガーされるアクションを定義する

[アクション] ドロップダウンをクリックし、[現在割り当てられている**関数はありません**] を選択し、[ **MeshRenderer** > **material material** ] を選択して、On Press () イベントがトリガーされたときに、キューブの material プロパティを変更するように設定します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

[素材] フィールドの横にある小さい**円**アイコン (現在は**None (素材)** が設定されている) をクリックして、[素材の選択] ウィンドウを開きます。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

[素材の選択] ウィンドウで**MRTK_Standard**を**検索**し、適切な素材を選択します。たとえば、ボタンが押されたときにキューブの色がシアンに変更されるように**MRTK_Standard_Cyan**します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6. On Release イベントを受け取るようにキューブを構成する

**繰り返し**On release イベントの手順4では、 **On release ()** イベントの受信者として**キューブ**を割り当てます。

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7. On Release イベントによってトリガーされるアクションを定義する

**繰り返し**On Release イベントの場合は手順5ですが、ボタンが離されたときにキューブの色が元の明るい灰色の色に戻るように**MRTK_Standard_LightGray**素材を選択します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8. エディター内シミュレーションを使用してボタンをテストする

**再生**ボタンを押してゲームモードに入り、エディター内入力シミュレーションを使用して、新しく構成されたボタンをテストします。

押されていないボタン (space + マウススクロールホイール後方):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

押されたボタン (space + マウスのホイールを前方にスクロール):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> エディター内入力シミュレーションの使用方法については、「エディターでの入力シミュレーションを使用して、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)でシーンガイドを[テストする](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)」を参照してください。

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>MRTK のグリッド オブジェクト コレクションを使用したボタンのパネルの作成

このセクションでは、MRTK の Grid オブジェクトコレクションツールを使用して、複数のボタンを適切なユーザーインターフェイスに自動的に配置する方法について説明します。

この例では、水平方向に配置された5つのボタンを持つパネルを作成する方法を示します。 ただし、同じ原則に従って他のレイアウトを作成することもできます。

これを実現するには、主に次の手順を実行します。

1. 親オブジェクトに対するボタンオブジェクトの親
2. Grid オブジェクトコレクション (スクリプト) コンポーネントの追加と構成
3. エディター内シミュレーションを使用してボタンをテストする

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1. 親オブジェクトにボタンオブジェクトを親とする

階層 ウィンドウ内の空の場所を右クリックし、**空の作成** を選択します。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

新しく作成したオブジェクトを右クリックし、 **[名前の変更]** を選択して、適切な名前を指定します (例: **buttoncollection**)。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

**PressableButtonHoloLens2**オブジェクトを選択し、 **buttoncollection**オブジェクトの上に**ドラッグ**して、buttoncollection オブジェクトの子にします。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

**PressableButtonHoloLens2**オブジェクトを右クリックし、 **[複製]** を選択してコピーを作成します。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

合計5つの PressableButtonHoloLens2 オブジェクトが表示されるまで、この手順をさらに4回**繰り返し**ます。

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. Grid オブジェクトコレクション (スクリプト) コンポーネントを追加して構成する

階層 ウィンドウで ButtonCollection オブジェクトを選択した状態で、インスペクター ウィンドウで **コンポーネントの追加** ボタンをクリックし、**grid オブジェクト**コレクション を検索して選択します。これにより、Grid オブジェクトコレクション (スクリプト) コンポーネントが buttoncollection オブジェクトに追加されます。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

次のように、Grid オブジェクトコレクション (スクリプト) を構成します。

* **[Num Rows]** を1に変更すると、すべてのボタンが1つの行に合わせて調整されます。
* **セルの幅**を0.05 に変更して、行内のボタンを空白にします。

次に、 **[コレクションの更新]** ボタンをクリックして、新しい構成を適用します。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> 適用した構成の変更は、ボタンを単一行に配置する目的を達成するために必要な最小限の変更を表します。 ただし、今後のプロジェクトでは、親オブジェクトや子オブジェクトの向きなどの要因によっては、たとえば、方向の種類など、他の設定の調整が必要になる場合があります。 MRTK の Grid オブジェクトコレクションの詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[オブジェクトコレクションスクリプト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts)に関するガイドを参照してください。

[階層] ウィンドウで [ButtonCollection] オブジェクトを選択した状態で、[インスペクター] ウィンドウの ButtonCollection オブジェクトの [変換**位置**] を変更して、子ボタンオブジェクトが、原点に配置されるカメラの前に配置されるようにします。たとえば、x = 0、y = 0、z = 0.5 のようになります。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> 前の「[ハンドトラッキングジェスチャと対話型 buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 」セクションでシーンに PressableButtonHoloLens2 prefab を初めて追加したときに、カメラの前に配置しました。 ただし、Grid オブジェクトコレクションはその直接の子オブジェクトの位置を制御するので、親値0からのグリッドオブジェクトコレクションの既定の距離に従って、PressableButtonHoloLens2 子オブジェクトの Z 位置が0にリセットされました。 これにより、親/子の位置関係を整理したままにするために、親の ButtonCollection オブジェクトの位置を前方に移動するのは、親の値からの距離を構成するのではなく、PressableButtonHoloLens2 の子オブジェクトを前方に移動するためです。

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3. エディター内シミュレーションを使用してボタンをテストする

再生ボタンを押してゲームモードに入り、エディター内入力シミュレーションを使用して、新しく作成されたボタンのパネルにあるの各ボタンをテストします。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> 現在、5つのボタンのいずれかを押すと、キューブの色が水色に変わります。 エクスペリエンスをさらに興味深いものにするために、ここで学習したことを使用して、キューブを別の色に変更するように各ボタンを構成します。

## <a name="adding-text-into-your-scene"></a>シーンへのテキストの追加

このセクションでは、Unity の TextMesh Pro を使用して、mixed reality エクスペリエンスにテキストを追加する方法について説明します。これは、前のチュートリアルの「 [Textmesh pro の重要なリソースのインポート](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)」セクションで準備したものです。

この例では、前のセクションで作成したボタンコレクションの下に単純なラベルを追加します。

ButtonCollection オブジェクトを右クリックし、[ **3D オブジェクト** > **TextMeshPro** ] を選択して、TextMeshPro オブジェクトを buttoncollection オブジェクトの子として作成します。

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

新しく作成された TextMeshPro オブジェクト (TMP) を選択したまま、[インスペクター] ウィンドウで、ボタンコレクションの下にラベルが表示されるように、その位置とサイズを変更します。次に例を示します。

* Rect 変換**Pos Y**を-0.0425 に変更します。
* 四角形の変換**幅**を0.24 に変更します
* 四角形の変換の**高さ**を0.024 に変更します。

次に、ラベルの内容を反映するようにテキストを更新し、テキストがラベル内に収まるようにフォントプロパティを選択します。次に例を示します。

* Text メッシュ Pro (スクリプト)**テキスト**をボタンコレクションに変更する
* Text メッシュ Pro (スクリプト) の**フォントスタイル**を太字に変更する
* Text メッシュ Pro (スクリプト) の**フォントサイズ**を0.2 に変更します。
* Text メッシュ Pro (スクリプト) の**配置**を中央および中央に変更する

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>結論

このチュートリアルでは、MRTK プロファイル設定を複製、カスタマイズ、および構成する方法について学習しました。 また、HoloLens 2 で追跡されたハンズオンを使用してイベントをトリガーするボタンを操作する方法についても学習しました。 最後に、MRTK の Grid オブジェクトコレクションコンポーネントと Unity のテキストメッシュ Pro を使用して、単純な UI インターフェイスを作成する方法について学習しました。

[次のチュートリアル: 4. 動的なコンテンツを配置し、ソルバーを使用する](mrlearning-base-ch3.md)
