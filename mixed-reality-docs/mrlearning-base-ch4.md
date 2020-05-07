---
title: 入門チュートリアル - 5. 3D オブジェクトの操作
description: 3D オブジェクトの整理や基本操作のための境界ボックスなど、基本的な 3D コンテンツとユーザー エクスペリエンスについて説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: b807ac7e51e4009d2c44d3b7c67fbdf3488ccbd9
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604993"
---
# <a name="5-interacting-with-3d-objects"></a>5.3D オブジェクトの操作

このチュートリアルでは、コレクションの一部としての 3D オブジェクトの整理、基本操作のための境界ボックス、近距離操作と遠距離操作、手の追跡によるタッチやグラブ ジェスチャなど、基本的な 3D コンテンツとユーザー エクスペリエンスについて説明します。

## <a name="objectives"></a>目標

* 他の学習目的に使用される 3D オブジェクトのパネルを作成する
* 境界ボックスを実装する
* 移動、回転、拡大縮小などの基本操作のための 3D オブジェクトを構成する
* 近距離操作と遠距離操作について確認する
* グラブやタッチなどのその他の手の追跡のジェスチャについて学習する

## <a name="importing-the-tutorial-assets"></a>チュートリアルのアセットのインポート

Unity カスタム パッケージをダウンロードしてインポートします。

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)

チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> Unity カスタム パッケージをインポートする方法については、「[Mixed Reality ツールキットをインポートする](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」の手順を参照してください。

## <a name="decluttering-the-scene-view"></a>シーン ビューの整理

シーンを簡単に操作できるようにするには、 **Cube** および **ButtonCollection** オブジェクトの左側にある**目**のアイコンをクリックして、それらのオブジェクトの**シーンの可視性**をオフに設定します。 これにより、ゲーム中の可視性を変更することなく、[Scene]\(シーン\) ウィンドウ内のオブジェクトが非表示になります。

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> シーンの可視性コントロールと、それらを使用してシーン ビューやワークフローを最適化する方法の詳細については、Unity の <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">シーンの可視性</a>に関するドキュメントを参照してください。

## <a name="organizing-3d-objects-in-a-collection"></a>コレクション内の 3D オブジェクトを整理する

このセクションでは、このチュートリアルの後続のセクションで 3D オブジェクトを操作するさまざまな方法を調べるときに使用する、3D オブジェクトのパネルを作成します。 具体的には、3D オブジェクトが 3 x 3 グリッドに配置されるように構成します。

[ボタンのパネルを作成した](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)ときと同様に、これを実現するための主な手順は次のとおりです。

1. 3D オブジェクトを親オブジェクトにペアレント化する
2. Grid Object Collection (Script) コンポーネントを追加して構成する

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1.3D オブジェクトを親オブジェクトにペアレント化する

[Hierarchy]\(階層\) ウィンドウで **空のオブジェクトを作成**し、適切な名前 (たとえば、**3DObjectCollection**) を付け、適切な場所 (たとえば、X = 0、Y = -0.2、Z = 2) に配置します。

[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)** に移動し、次のプレハブを **3DObjectCollection** に**ペアレント化します**。

* Cheese
* CoffeeCup
* EarthCore
* Octa
* Platonic
* TheModule

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

[Hierarchy]\(階層\) ウィンドウで、**3DObjectCollection** の子オブジェクトとして **3 つのキューブを作成**し、[Transform]\(変換\) の **[Scale]\(スケール\)** を X = 0.15、Y = 0.15、Z = 0.15 に設定します。

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> 上記の手順を実行する方法については、「[ユーザー インターフェイスの作成と Mixed Reality ツールキットの構成](mrlearning-base-ch2.md)」チュートリアルを参照してください。

各キューブが表示されるように、キューブを再配置します。

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MixedRealityToolkit.SDK]**  >  **[StandardAssets]**  >  **[Materials]\(素材\)** に移動し、MRTK で提供されている素材を確認します。

各キューブの [Mesh Renderer]\(メッシュ レンダラー\) の **[Materials]\(素材\)** の [Element 0]\(要素 0\) プロパティに適切な素材を**クリックしてドラッグします**。次に例を示します。

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2.Grid Object Collection (Script) コンポーネントを追加して構成する

**Grid Object Collection (Script)** コンポーネントを **3DObjectCollection** オブジェクトに追加し、次のように構成します。

* **[Sort Type]\(並べ替えの種類\)** を **[Child Order]\(子の順序\)** に変更して、子オブジェクトが、親オブジェクトの下に配置した順序で並べ替えられるようにします。

次に、 **[Update Collection]\(コレクションの更新\)** ボタンをクリックして、新しい構成を適用します。

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>3D オブジェクトの操作

このセクションでは、前のセクションで作成したパネル内のすべての 3D オブジェクトを操作する機能を追加します。 またプレハブ オブジェクトの場合は、ユーザーが追跡対象の手を使用して、これらのオブジェクトに手を伸ばしてつかむことができるようにします。 次に、オブジェクトに適用できる操作動作をいくつか確認します。

これを実現するための主な手順は次のとおりです。

1. すべてのオブジェクトに Manipulation Handler (Script) コンポーネントを追加する
2. プレハブ オブジェクトに Near Interaction Grabbable (Script) コンポーネントを追加する
3. Manipulation Handler (Script) コンポーネントを構成する

> [!IMPORTANT]
> **オブジェクトを操作**できるようにするには、オブジェクトに次のコンポーネントが必要です。
>
> * **Collider** コンポーネント、たとえばボックス コライダー
> * **Manipulation Handler (Script)** コンポーネント
>
> オブジェクトを**操作**し、**追跡対象の手でオブジェクトをつかむ**ことができるようにするには、オブジェクトに次のコンポーネントが必要です。
>
> * **Collider** コンポーネント、たとえばボックス コライダー
> * **Manipulation Handler (Script)** コンポーネント
> * **Near Interaction Grabbable (Script)** コンポーネント

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1.すべてのオブジェクトに Manipulation Handler (Script) コンポーネントを追加する

[Hierarchy]\(階層\) ウィンドウで、 **[Cheese]** オブジェクトを選択し、**Shift** キーを押したまま **[Cube () 2]** オブジェクトを選択し、すべてのオブジェクトに **Manipulation Handler (Script)** コンポーネントを追加します。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> このチュートリアルでは、コライダーが既にプレハブに追加されています。 Cube オブジェクトなどの Unity プリミティブの場合、オブジェクトが作成されるときに Collider コンポーネントが自動的に追加されます。 上の図では、コライダーは緑色のアウトラインで示されています。 コライダーの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">コライダー</a>に関するドキュメントを参照してください。

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2.プレハブ オブジェクトに Near Interaction Grabbable (Script) コンポーネントを追加する

[Hierarchy]\(階層\) ウィンドウで、 **[Cheese]** オブジェクトを選択し、**Shift** キーを押したまま **[TheModule]** オブジェクトを選択し、すべてのオブジェクトに **Near Interaction Grabbable (Script)** コンポーネントを追加します。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3.Manipulation Handler (Script) コンポーネントを構成する

#### <a name="default-manipulation"></a>既定の操作

**Cube** オブジェクトについて、既定の操作の動作を実行するために、すべてのプロパティを既定のままにします。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> コンポーネントを既定値にリセットするには、コンポーネントの [Settings]\(設定\) アイコンを選択して [Reset]\(リセット\) を選択します。

#### <a name="restrict-manipulation-to-scale-only"></a>操作をスケールのみに制限する

**Cube (1)** オブジェクトについて、 **[Two Handed Manipulation Type]\(両手を使った操作の種類\)** を **[Scale]\(スケール\)** に変更し、ユーザーがオブジェクトのサイズのみを変更できるようにします。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>移動をユーザーから一定の距離に制限する

**Cube (2)** オブジェクトについて、 **[Constraint On Movement]\(動きの制限\)** を **[Fix Distance From Head]\(頭部から一定の距離\)** に変更して、オブジェクトを移動したときに、それがユーザーから同じ距離を保つようにします。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>既定のグラブ可能な操作

**Cheese**、**CoffeCup**、および **EarthCore** オブジェクトについて、すべてのプロパティを既定のままにして、既定のグラブ可能な操作の動作を実行します。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>遠距離操作機能を除去する

**Octa** オブジェクトについて、 **[Allow Far Manipulation]\(遠距離操作を許可\)** チェック ボックスをオフにして、ユーザーが追跡対象の手を使用した場合のみオブジェクトを直接操作できるようにします。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>オブジェクトを中心を軸に回転させる

**Platonic** オブジェクトについて、 **[One Hand Rotation Mode Near]\(片手回転モード - 近距離\)** および **[One Hand Rotation Mode Far]\(片手回転モード - 遠距離\)** を **[Rotate About Object Center]\(オブジェクトの中心を軸に回転\)** に変更し、ユーザーがオブジェクトを 1 つの手で回転させたとき、オブジェクトが中心を軸に回転するようにします。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a>オブジェクトを放した後も動作を続ける

**TheModule** オブジェクトについて、**Rigidbody** コンポーネントを追加して物理的処理を有効にし、 **[Use Gravity]\(重力を使用\)** チェックボックスをオフにして、オブジェクトが重力の影響を受けないようにします。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

Manipulation Handler (Script) コンポーネントに戻り、 **[Release Behavior]\(解放動作\)** が **[Keep Velocity]\(速度を維持\)** および **[Keep Angular Velocity]\(角速度を維持\)** の両方に設定されていることを確認し、オブジェクトがユーザーの手から離れた後も動き続けるようにします。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

Manipulation Handler コンポーネントとその関連プロパティの詳細については、[MRTK ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[操作ハンドラー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)に関するガイドを参照してください。

## <a name="adding-bounding-boxes"></a>境界ボックスの追加

境界ボックスには、拡大縮小および回転に使用できるハンドルが用意されているため、1 つの手で、近距離と遠距離の両方のオブジェクトを操作するのがより簡単かつ直感的になります。

この例では、EarthCore オブジェクトに境界ボックスを追加して、前のセクションで構成したオブジェクト操作、および境界ボックスのハンドルを使用した拡大縮小と回転を使用して、このオブジェクトを操作できるようにします。

> [!IMPORTANT]
> **境界ボックス**を使用できるようにするには、オブジェクトに次のコンポーネントが必要です。
>
> * **Collider** コンポーネント、たとえばボックス コライダー
> * **Bounding Box (Script)** コンポーネント

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1.Bounding Box (Script) コンポーネントを EarthCore オブジェクトに追加する

[Inspector]\(インスペクター\) ウィンドウで **[EarthCore]** オブジェクトを選択し、**Bounding Box (Script)** コンポーネントを EarthCore オブジェクトに追加します。

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> 境界ボックスの視覚エフェクトは実行時に作成されるため、ゲーム モードに入る前は表示されません。

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2.エディター内のシミュレーションを使用して境界ボックスを視覚化およびテストする

[Play]\(再生\) ボタンを押してゲーム モードに入ります。 次に、スペースキーを押して保持することで手を表示し、マウスを使用して境界ボックスを操作します。

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

Bounding Box コンポーネントとその関連プロパティの詳細については、[MRTK ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[境界ボックス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)に関するガイドを参照してください。

## <a name="adding-touch-effects"></a>タッチ エフェクトの追加

この例では、手でオブジェクトに触れたときにイベントがトリガーされるようにします。 具体的には、ユーザーが触れたときにサウンド エフェクトが再生されるように Octa オブジェクトを構成します。

これを実現するための主な手順は次のとおりです。

1. オブジェクトに Audio Source コンポーネントを追加する
2. オブジェクトに Near Interaction Touchable (Script) コンポーネントを追加する
3. オブジェクトに Hand Interaction Touch (Script) コンポーネントを追加する
4. On Touch Started イベントを実装する
5. エディター内のシミュレーションを使用してタッチ操作をテストする

> [!IMPORTANT]
> **タッチ イベントをトリガー**できるようにするには、オブジェクトに次のコンポーネントが必要です。
>
> * **Collider** コンポーネント、可能であればボックス コライダー
> * **Near Interaction Touchable (Script)** コンポーネント
> * **Hand Interaction Touch (Script)** コンポーネント

> [!NOTE]
> Hand Interaction Touch (Script) コンポーネントは MRTK の一部ではありません。 これはこのチュートリアルのアセットと共にインポートされ、もともとは Mixed Reality ツールキットの Unity の例の一部でした。

### <a name="1-add-an-audio-source-component-to-the-object"></a>1.オブジェクトに Audio Source コンポーネントを追加する

[Hierarchy]\(階層\) ウィンドウで、 **[Octa]** オブジェクトを選択し、**Audio Source** コンポーネントを Octa オブジェクトに追加します。次に、 **[Spatial Blend]\(空間ブレンド\)** を 1 に変更して、空間オーディオを有効にします。

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2.オブジェクトに Near Interaction Touchable (Script) コンポーネントを追加する

**[Octa]** オブジェクトが選択された状態で、**Near Interaction Touchable (Script)** コンポーネントを Octa オブジェクトに追加します。次に、 **[Fix Bounds]\(境界の修正\)** および **[Fix Center]\(センターの修正\)** ボタンをクリックして、Near Interaction Touchable (Script) の [Local Center]\(ローカルのセンター\) および [Bounds]\(境界\) のプロパティを BoxCollider に一致するように更新します。

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3.オブジェクトに Hand Interaction Touch (Script) コンポーネントを追加する

**[Octa]** オブジェクトを選択した状態で、**Hand Interaction Touch (Script)** コンポーネントを Octa オブジェクトに追加します。

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4.On Touch Started イベントを実装する

**Hand Interaction Touch (Script)** コンポーネントで、小さい **+** アイコンをクリックして、新しい **On Touch Started ()** イベントを作成します。 次に、イベントを受信するように **Octa** オブジェクトを構成し、トリガーされるアクションとして **AudioSource.PlayOneShot** を定義します。

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

**[Assets]\(アセット\)**  >  **[MixedRealityToolkit.SDK]**  >  **[StandardAssets]**  >  **[Audio]\(オーディオ\)** に移動して、MRTK で提供されているオーディオ クリップを表示します。次に、適切なオーディオ クリップ (MRTK_Gem オーディオ クリップなど) を **[Audio Clip]\(オーディオ クリップ\)** フィールドに割り当てます。

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> イベントを実装する方法については、「[手の追跡のジェスチャと操作可能なボタン](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)」の説明を参照してください。

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5.エディター内のシミュレーションを使用してタッチ操作をテストする

[Play]\(再生\) ボタンを押してゲーム モードに入ります。 次に、スペースキーを押して保持することで手を表示し、マウスを使用して Octa オブジェクトに触れてサウンド エフェクトをトリガーします。

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> タッチ操作のテスト時に見られるように、また上の図に示すように、Octa オブジェクトに触れている間、その色は脈打つように変化します。 このエフェクトは、前述の手順で実行したイベント構成の結果ではなく、Hand Interaction Touch (Script) コンポーネントにハード コーディングされています。
>
> このエフェクトを無効にする場合は、たとえば 32 行目の 'TargetRenderer = GetComponentInChildren<Renderer>();' をコメントアウトすると、TargetRenderer が null のままになり、色は脈打つように変化しません。

## <a name="congratulations"></a>結論

このチュートリアルでは、3D オブジェクトをグリッド コレクションに整理する方法と、近距離操作 (追跡対象の手で直接グラブ) と遠距離操作 (視線または手の光線を使用) を使用してこれらのオブジェクトを操作 (拡大縮小、回転、および移動) する方法を学習しました。 また、3D オブジェクトの周りに境界ボックスを配置する方法と、境界ボックスのハンドルの使用とカスタマイズの方法についても学習しました。 最後に、オブジェクトにタッチしたときにイベントをトリガーする方法を学習しました。

[次のレッスン:6.高度な入力オプションの探索](mrlearning-base-ch5.md)
