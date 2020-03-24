---
title: 入門チュートリアル - 3. ユーザー インターフェイスの作成と Mixed Reality Toolkit の構成
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376139"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3.ユーザー インターフェイスの作成と Mixed Reality Toolkit の構成
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

前のチュートリアルでは、HoloLens 2 の最初のアプリケーションを開始することにより、Mixed Reality Toolkit (MRTK) で提供されている機能のいくつかを学習しました。 このチュートリアルでは、ボタンを UI テキスト パネルと共に作成して整理し、既定の対話式操作 (タッチ) を使用して各ボタンを操作する方法を学習します。 また、オブジェクトのサイズ、音、色の変更など、単純なアクションや効果の追加も調査します。 このモジュールでは、[空間マッピング](spatial-mapping.md) メッシュの可視化をオフにすることから始めて、MRTK プロファイルの変更に関する基本的な概念を紹介します。

## <a name="objectives"></a>目標

* Mixed Reality ツールキット プロファイルをカスタマイズおよび構成する
* UI 要素とボタンを使用してホログラムを操作する
* 基本的な手の追跡の入力と操作

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Mixed Reality Toolkit プロファイルを構成する方法 (空間認識の表示オプションの変更)
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

このセクションでは、既定の MRTK プロファイルをカスタマイズして構成する方法について説明します。

この特定の例では、空間メッシュ オブザーバーの設定を変更して、空間認識メッシュを非表示にする方法を示します。 ただし、次の同じ原則に従って、MRTK プロファイルのすべての設定または値をカスタマイズできます。

空間認識メッシュを非表示にするための主な手順は次のとおりです。

1. 既定の構成プロファイルを複製する
2. 空間認識システムを有効にする
3. 既定の空間認識システムのプロファイルを複製する
4. 既定の空間認識メッシュ オブザーバーのプロファイルを複製する
5. 空間認識メッシュの可視性を変更する

> [!NOTE]
> 既定では、MRTK プロファイルは編集できません。 これらは、編集する前に複製する必要がある既定プロファイルのテンプレートです。 入れ子になったプロファイル レイヤーがいくつかあります。 そのため、1 つ以上の設定を構成するときは、複数のプロファイルを複製して編集するのが一般的です。

### <a name="1-clone-the-default-configuration-profile"></a>1.既定の構成プロファイルを複製する

> [!NOTE]
> 構成プロファイルは最上位のプロファイルです。 そのため、他のプロファイルを編集できるようにするには、まず構成プロファイルを複製する必要があります。

[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで、Mixed Reality Toolkit の**構成プロファイル**を **[DefaultHoloLens2ConfigurationProfile]** に変更します。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

**MixedRealityToolkit** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Copy & Customize]\(コピーしてカスタマイズ\)** ボタンをクリックして、[Clone Profile]\(プロファイルの複製\) ウィンドウを開きます。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

[Clone Profile]\(プロファイルの複製\) ウィンドウで **[Clone]\(複製\)** ボタンをクリックして、**DefaultHololens2ConfigurationProfile** の編集可能なコピーを作成します。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

新しく作成された構成プロファイルが、シーンの構成プロファイルとして割り当てられました。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

Unity メニューで、 **[File]\(ファイル\)**  >  **[Save]\(保存\)** の順に選択してシーンを保存します。

> [!TIP]
> チュートリアルの実行中は、必ず作業を保存するようにしてください。

### <a name="2-enable-the-spatial-awareness-system"></a>2.空間認識システムを有効にする

[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Spatial Awareness]\(空間認識\)** タブを選択し、次に **[Enable Spatial Awareness System]\(空間認識システムを有効にする\)** チェックボックスをオンにします。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3.既定の空間認識システムのプロファイルを複製する

**[Spatial Awareness]\(空間認識\)** タブで、 **[Clone]\(複製\)** ボタンをクリックして [Clone Profile]\(プロファイルの複製\) ウィンドウを開きます。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

[Clone Profile]\(プロファイルの複製\) ウィンドウで **[Clone]\(複製\)** ボタンをクリックして、**DefaultMixedRealitySpatialAwarenessSystemProfile** の編集可能なコピーを作成します。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

これで、新しく作成された空間認識システム プロファイルが、構成プロファイルに自動的に割り当てられるようになりました。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4.既定の空間認識メッシュ オブザーバーのプロファイルを複製する

**[Spatial Awareness]\(空間認識\)** タブを引き続き選択した状態で、 **[Windows Mixed Reality Spatial Mesh Observer]\(Windows Mixed Reality 空間メッシュ オブザーバー\)** セクションを展開し、 **[Clone]\(複製\)** ボタンをクリックして、[Clone Profile]\(プロファイルの複製\) ウィンドウを開きます。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

[Clone Profile]\(プロファイルの複製\) ウィンドウで **[Clone]\(複製\)** ボタンをクリックして、**DefaultMixedRealitySpatialAwarenessMeshObserverProfile** の編集可能なコピーを作成します。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

これで、新しく作成された空間認識メッシュ オブザーバーが、空間認識システム プロファイルに自動的に割り当てられるようになりました。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5.空間認識メッシュの可視性を変更する

**[Spatial Mesh Observer Settings]\(空間メッシュ オブザーバーの設定\)** で、 **[Display Option]\(表示オプション\)** を **[Occlusion]\(オクルージョン\)** に変更して、空間マッピング メッシュを、機能している状態のまま非表示にします。

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> 空間マッピング メッシュは非表示になっていますが、引き続き存在して、機能しています。 たとえば、物理的な壁の後ろのホログラムなど、空間マッピング メッシュの背後にあるホログラムは表示されません。

ここまで、MRTK プロファイル内の設定を変更する方法を学習しました。 ご覧のように、MRTK の設定をカスタマイズするには、最初に既定のプロファイルのコピーを作成する必要があります。 既定のプロファイルは編集できないため、既定の設定に戻す場合の参照として常に保持します。 MRTK プロファイルとそのアーキテクチャの詳細については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)にある「[Mixed Reality Toolkit プロファイルの構成ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)」をご覧ください。

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>ハンド トラッキングのジェスチャと対話可能なボタン

このセクションでは、ハンド トラッキングを使用してボタンを押し、ボタンが押されるとアクションを実行するイベントをトリガーする方法について説明します。

この特定の例では、ボタンを押すとキューブの色が変わり、ボタンを離すと元の色に戻るように変更する方法を示します。 ただし、次の同じ原則に従って他のイベントを作成することもできます。

キューブの色を変更するための主な手順は次のとおりです。

1. 押しボタンのプレハブをシーンに追加する
2. キューブをシーンに追加する
3. InteractableOnPressReceiver イベントの種類を構成する
4. On Press イベントを受け取るようにキューブを構成する
5. On Press イベントによってトリガーされるアクションを定義する
6. On Release イベントを受け取るようにキューブを構成する
7. On Release イベントによってトリガーされるアクションを定義する
8. エディター内シミュレーションを使用してボタンをテストする

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1.押しボタンのプレハブをシーンに追加する

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">プレハブ</a>は、Unity アセットとして格納されている事前構成済みの GameObject であり、プロジェクト全体で再利用できます。

**[Project]\(プロジェクト\) ウィンドウ**で **PressableButtonHoloLens2** を検索して、この例で使用するプレハブを見つけます。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

**検索**の結果から **[PressableButtonHoloLens2]** プレハブを選択し、 **[Hierarchy]\(階層\)** ウィンドウに**ドラッグ**してシーンに追加します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> 次の図に示すようにシーンを表示するには、[Hierarchy]\(階層\) ウィンドウで PressableButtonHoloLens2 オブジェクトをダブルクリックしてフォーカスを当て、[Scene]\(シーン\) ウィンドウの右上隅にある <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> を使用して、前の Z 軸に沿うように表示角度を調整します。

**PressableButtonHoloLens2** オブジェクトを引き続き選択した状態で、 **[Inspector]\(インスペクター\)** ウィンドウで次を実行します。

* [Transform]\(変換\) の **[Position]\(位置\)** を、原点に位置するカメラの前に配置されるように変更します (たとえば、x = 0、y = 0、z = 0.5)。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> 一般に、Unity での位置の単位 1 は、物理的世界のほぼ 1 m に相当します。 ただし、これには、あるオブジェクトがスケーリングされたオブジェクトの子である場合などの例外があります。

### <a name="2-add-a-cube-to-the-scene"></a>2.キューブをシーンに追加する

[Hierarchy]\(階層\) ウィンドウ内の何もない場所を右クリックし、 **[3D Object]\(3D オブジェクト\)**  >  **[Cube]** の順に選択して、キューブをシーンに追加します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

**Cube** オブジェクトを引き続き選択した状態で、 **[Inspector]\(インスペクター\)** ウィンドウで次を実行します。

* 押しボタンの近くになるように (ただし、重ならないように)、[Transform]\(変換\) の **[Position]\(位置\)** を変更します (たとえば、x = 0、y = 0.04、z = 0.5)。
* [Transform]\(変換\) の **[Scale]\(スケール\)** を適切なサイズに変更します (たとえば、x = 0.02、y = 0.02、z = 0.02)。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3.InteractableOnPressReceiver イベントの種類を構成する

[Hierarchy]\(階層\) ウィンドウで **PressableButtonHoloLens2** オブジェクトを選択し、次に **[Inspector]\(インスペクター\)** ウィンドウの **ハンバーガー メニュー**で **[Collapse All Components]\(すべてのコンポーネントを折りたたむ\)** を選択して、このオブジェクトのすべてのコンポーネントの概要を取得します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

**Interactable (Script)** コンポーネントを展開し、次に、 **[Events]\(イベント\)**  >  **[Receivers]\(レシーバー\)** セクションを見つけて展開します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

**[Add Event]\(イベントの追加\)** ボタンをクリックして、イベント レシーバーの種類 **InteractableOnPressReceiver** の新しいイベント レシーバーを作成します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> InteractableOnPressReceiver というイベント レシーバーの種類を使用すると、追跡対象のハンドがボタンを押したときに、押されたイベントにボタンが応答できるようになります。

新しく作成されたイベント レシーバーに対して、 **[Interaction Filter]\(対話式操作フィルター\)** を **[Near and Far]\(近くと遠く\)** に変更します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4.On Press イベントを受け取るようにキューブを構成する

[Hierarchy]\(階層\) ウィンドウから、**キューブ**を **On Press ()** イベントの **[Event Properties]** オブジェクト フィールドに**クリックアンドドラッグ**して、キューブを On Press () イベントのレシーバーとして割り当てます。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5.On Press イベントによってトリガーされるアクションを定義する

アクション ドロップダウン (現在は **[No Function]\(関数なし\)** が割り当てられている) をクリックし、 **[MeshRenderer]**  >  **[Material material]** の順に選択して、On Press () イベントがトリガーされたときにキューブのマテリアル プロパティが変更されるように設定します。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

現在 **[None (Material)]\(なし (マテリアル)\)** が設定されているマテリアル フィールドの横の小さな**円**のアイコンをクリックして、[Select Material]\(マテリアルの選択\) ウィンドウを開きます。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

[Select Material]\(マテリアルの選択\) ウィンドウで、**MRTK_Standard** を**検索**し、適切なマテリアルを選択します。たとえば、**MRTK_Standard_Cyan** を選択して、ボタンを押したときにキューブの色がシアンに変わるようにします。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6.On Release イベントを受け取るようにキューブを構成する

On Release イベントに対して手順 4 を**繰り返し**、**キューブ**を **On Release ()** イベントのレシーバーとして割り当てます。

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7.On Release イベントによってトリガーされるアクションを定義する

On Release イベントに対して手順 5 を**繰り返し**ます。ただし、**MRTK_Standard_LightGray** マテリアルを選択して、ボタンを離したときにキューブの色が元の薄い灰色に戻るようにします。

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8.エディター内シミュレーションを使用してボタンをテストする

**[Play]\(再生\)** ボタンを押してゲーム モードに入り、エディター内入力シミュレーションを使用して、新しく構成したボタンをテストします。

ボタンが押されていない (スペース バー + 後方へのマウスのスクロール ホイール):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

ボタンが押されている (スペース バー + 前方へのマウスのスクロール ホイール):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> エディター内入力シミュレーションの使用方法については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)で「[エディター内ハンド入力シミュレーションを使用したシーンのテスト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)」ガイドを参照してください。

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>MRTK の Grid Object Collection を使用したボタンのパネルの作成

このセクションでは、MRTK の Grid Object Collection ツールを使用して、整ったユーザー インターフェイスになるように複数のボタンを自動的に整列させる方法を学習します。

この特定の例では、5 つのボタンが水平方向に一列に整列したパネルを作成する方法を示します。 ただし、次の同じ原則に従って他のレイアウトを作成することもできます。

これを実現するための主な手順は次のとおりです。

1. ボタン オブジェクトを親オブジェクトに従属させる
2. Grid Object Collection (Script) コンポーネントを追加して構成する
3. エディター内シミュレーションを使用してボタンをテストする

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1.ボタン オブジェクトを親オブジェクトに従属させる

[Hierarchy]\(階層\) ウィンドウ内の何もない場所を右クリックし、 **[Create Empty]\(空の作成\)** を選択します。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

新しく作成されたオブジェクトを右クリックし、 **[Rename]\(名前の変更\)** を選択して、適切な名前を付けます (たとえば、**ButtonCollection**)。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

**PressableButtonHoloLens2** オブジェクトを選択し、それを **ButtonCollection** オブジェクトの上に**ドラッグ**して、ButtonCollection オブジェクトの子にします。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

**PressableButtonHoloLens2** オブジェクトを右クリックし、 **[Duplicate]\(複製\)** を選択してコピーを作成します。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

合計 5 つの PressableButtonHoloLens2 オブジェクトを取得するまで、この手順をさらに 4 回**繰り返し**ます。

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2.Grid Object Collection (Script) コンポーネントを追加して構成する

[Hierarchy]\(階層\) ウィンドウで ButtonCollection オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンをクリックし、次に **Grid Object Collection** を検索して選択し、Grid Object Collection (Script) コンポーネントを ButtonCollection オブジェクトに追加します。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

次のように、Grid Object Collection (Script) を構成します。

* **[Num Rows]\(行数\)** を 1 に変更して、すべてのボタンを 1 行に整列させる
* **[Cell Width]\(セル幅\)** を 0.05 に変更して、行内でボタンを一定間隔で並べる

次に、 **[Update Collection]\(コレクションの更新\)** ボタンをクリックして、新しい構成を適用します。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> たった今適用した構成変更は、ボタンを 1 行に配置するという目的を達成するために必要な最小限の変更を表しています。 ただし、今後のプロジェクトでは、たとえば、親と子のオブジェクトの向きなどの要因によっては、方向の種類など、他の設定の調整が必要になることもあります。 MRTK の Grid Object Collection の詳細については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)にある「[Object Collection スクリプト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts)」のガイドを参照してください。

[Hierarchy]\(階層\) ウィンドウで ButtonCollection オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで、ButtonCollection オブジェクトの [Transform]\(変換\) の **[Position]\(位置\)** を変更して、子ボタン オブジェクトがカメラの前に配置されるようにします (原点では、たとえば、x = 0、y = 0、z = 0.5 に配置されている)。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> 上記の「[ハンド トラッキングのジェスチャと対話可能なボタン](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)」セクションで PressableButtonHoloLens2 プレハブを初めてシーンに追加したときに、それをカメラの前に配置しました。 ただし、Grid Object Collection はその直接の子オブジェクトの位置を制御するので、PressableButtonHoloLens2 子オブジェクトの Z 位置は、Grid Object Collection での親値からの既定距離 0 に従って、0 にリセットされました。 このことにより、また、親/子の位置関係を整理しておくために、PressableButtonHoloLens2 子オブジェクトを前方に移動するように親値からの距離を構成するのではなく、親の ButtonCollection オブジェクトの位置を前方に移動しました。

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3.エディター内シミュレーションを使用してボタンをテストする

[Play]\(再生\) ボタンを押してゲーム モードに入り、エディター内入力シミュレーションを使用して、新しく作成したボタンのパネルで各ボタンをテストします。

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> 現在、5 つのボタンのいずれかを押すと、キューブの色がシアンに変わります。 エクスペリエンスをさらにおもしろくするために、たった今学習したことを使用して、キューブが別の色に変わるように各ボタンを構成します。

## <a name="adding-text-into-your-scene"></a>シーンへのテキストの追加

このセクションでは、前のチュートリアルの「[TextMesh Pro の Essential Resources (重要なリソース) をインポートする](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)」セクションで準備した Unity の TextMesh Pro を使用して、Mixed Reality エクスペリエンスにテキストを追加する方法を学習します。

この特定の例では、前のセクションで作成したボタン コレクションの下に単純なラベルを追加します。

ButtonCollection オブジェクトを右クリックし、 **[3D Object]\(3D オブジェクト\)**  >  **[Text - TextMeshPro]\(テキスト - TextMeshPro\)** を選択して、ButtonCollection オブジェクトの子として TextMeshPro オブジェクトを作成します。

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

Text (TMP) という名前の新しく作成された TextMeshPro オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで、その位置とサイズを変更して、ラベルがボタン コレクションの下に正しく表示されるようにします。たとえば、次のようにします。

* [Rect Transform]\(四角形の変換\) の **[Pos Y]\(位置 Y\)** を -0.0425 に変更する
* [Rect Transform]\(四角形の変換\) の **[幅]** を 0.24 に変更する
* [Rect Transform]\(四角形の変換\) の **[高さ]** を 0.024 に変更する

次に、ラベルの内容を反映するようにテキストを更新し、テキストがラベル内に収まるようにフォント プロパティを選択します。たとえば、次のようにします。

* Text Mesh Pro (Script) の **[Text]\(テキスト\)** を Button Collection に変更する
* Text Mesh Pro (Script) の **[Font Style]\(フォント スタイル\)** を太字に変更する
* Text Mesh Pro (Script) の **[Font Size]\(フォント サイズ\)** を 0.2 に変更する
* Text Mesh Pro (Script) の **[Alignment]\(配置\)** を中央揃え中央に変更する

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>結論

このチュートリアルでは、MRTK プロファイルの設定を複製、カスタマイズ、および構成する方法について学習しました。 また、HoloLens 2 で追跡対象のハンドを使用してイベントをトリガーするようにボタンを操作する方法も学習しました。 最後に、MRTK の Grid Object Collection コンポーネントと Unity の Text Mesh Pro を使用して単純な UI インターフェイスを作成する方法を学習しました。

[次のチュートリアル:4.動的なコンテンツの配置とソルバーの使用](mrlearning-base-ch3.md)
