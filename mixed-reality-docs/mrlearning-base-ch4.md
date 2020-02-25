---
title: 入門チュートリアル-5. 3D オブジェクトとの対話
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 7eb38e205237257e400550299fdeebb73ba746f1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555499"
---
# <a name="5-interacting-with-3d-objects"></a>5. 3D オブジェクトとの対話

このチュートリアルでは、基本的な3D コンテンツとユーザーエクスペリエンスについて学習します。これには、コレクションの一部としての3D オブジェクトの整理、基本的な操作のための境界ボックス、近辺と遠くの対話、およびハンドトラッキングによるタッチやグラブのジェスチャなどが含まれます。

## <a name="objectives"></a>目標

* 他の学習目的に使用される3D オブジェクトのパネルを作成する
* 境界ボックスを実装する
* 移動、回転、拡大/縮小などの基本的な操作のために3D オブジェクトを構成する
* 近距離操作と遠距離操作について確認する
* グラブやタッチなど、その他のハンドトラッキングジェスチャについて説明します。

## <a name="importing-the-tutorial-assets"></a>チュートリアル資産のインポート

Unity カスタムパッケージをダウンロードしてインポートします。

* [MRTK。HoloLens2. 2.3.0.2. unitypackage を実行します。](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

チュートリアルのアセットをインポートすると、プロジェクトウィンドウは次のようになります。

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> Unity カスタムパッケージをインポートする方法については、「 [Mixed Reality Toolkit のインポート](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」の手順を参照してください。

## <a name="decluttering-the-scene-view"></a>シーンビューの Decluttering

シーンを簡単に操作できるようにするには、オブジェクトの左側にある**目**のアイコンをクリックして、**キューブ**および**buttoncollection**オブジェクトの**シーンの表示**をオフに設定します。 これにより、シーンウィンドウ内のオブジェクトが非表示になります。ゲーム中の可視性は変更されません。

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> シーンの可視性の制御とそれらを使用してシーンビューやワークフローを最適化する方法の詳細については、Unity の<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">シーンの可視性</a>に関するドキュメントを参照してください。

## <a name="organizing-3d-objects-in-a-collection"></a>コレクション内の3D オブジェクトの整理

このセクションでは、このチュートリアルの次のセクションで3D オブジェクトを操作するさまざまな方法を調べるときに使用する、3D オブジェクトのパネルを作成します。 具体的には、3D オブジェクトが 3 x 3 グリッドに配置されるように構成します。

[ボタンのパネルを作成](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)したときと同様に、これを実現するための主要な手順は次のとおりです。

1. 親オブジェクトへの3D オブジェクトの親
2. Grid オブジェクトコレクション (スクリプト) コンポーネントの追加と構成

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1. 3D オブジェクトを親オブジェクトに親します。

[階層] ウィンドウで、**空のオブジェクトを作成**し、適切な名前 (たとえば、 **3DObjectCollection**) を指定し、適切な場所に配置します (例: X = 0、Y =-0.2、Z = 2)。

[プロジェクト] ウィンドウで、[**アセット** > **mrtk] に移動します。チュートリアル: GettingStarted** **Prefabs**を開始し、次の Prefabs を**3DObjectCollection**に**親**とします。 > 

* 頭
* CoffeeCup
* EarthCore
* Octa
* プラトニック
* モジュール

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

[階層] ウィンドウで、 **3DObjectCollection**の子オブジェクトとして**3 つのキューブを作成**し、変換の**スケール**を X = 0.15、Y = 0.15、Z = 0.15 に設定します。

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> 上記の手順を実行する方法については、「[ユーザーインターフェイスの作成」および「Mixed Reality Toolkit の構成](mrlearning-base-ch2.md)」のチュートリアルを参照してください。

各キューブを表示できるように、キューブの位置を変更します。

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

[プロジェクト] ウィンドウで、[**資産** > **MixedRealityToolkit** > **standardassets** > **マテリアル**] に移動し、mrtk で提供されている素材を確認します。

次の例のように、適切な素材を各キューブのメッシュ**レンダラーの**要素0プロパティに**ドラッグ**アンドドロップします。

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. Grid オブジェクトコレクション (スクリプト) コンポーネントを追加して構成する

**Grid オブジェクトコレクション (スクリプト)** コンポーネントを**3DObjectCollection**オブジェクトに追加し、次のように構成します。

* 子オブジェクトが親オブジェクトの下に配置された順序で並べ替えられるようにするには、 **[並べ替えの種類]** を **[子の順序]** に変更します。

次に、 **[コレクションの更新]** ボタンをクリックして、新しい構成を適用します。

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>3D オブジェクトの操作

このセクションでは、前のセクションで作成したパネル内のすべての3D オブジェクトを操作する機能を追加します。 さらに、prefab オブジェクトの場合は、ユーザーが追跡したハンドを使用してこれらのオブジェクトを取得して取得できるようにします。 次に、オブジェクトに適用できるいくつかの操作の動作について説明します。

これを実現するには、主に次の手順を実行します。

1. すべてのオブジェクトに操作ハンドラー (スクリプト) コンポーネントを追加します。
2. Near 相互作用 Grabbable (スクリプト) コンポーネントを prefab オブジェクトに追加します。
3. 操作ハンドラー (スクリプト) コンポーネントの構成

> [!IMPORTANT]
> **オブジェクトを操作**できるようにするには、オブジェクトに次のコンポーネントが必要です。
>
> * **Collider**コンポーネント (Box collider など)
> * **操作ハンドラー (スクリプト)** コンポーネント
>
> **追跡したハンドを使用**してオブジェクトを**操作**および取得できるようにするには、オブジェクトに次のコンポーネントが含まれている必要があります。
>
> * **Collider**コンポーネント (Box collider など)
> * **操作ハンドラー (スクリプト)** コンポーネント
> * **Near 相互作用 Grabbable (スクリプト)** コンポーネント

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1. 操作ハンドラー (スクリプト) コンポーネントをすべてのオブジェクトに追加します。

階層 ウィンドウで、**チーズ** オブジェクトを選択し、 **shift**キーを押しながら、 **Cube () 2**オブジェクトを選択して、**操作ハンドラー (スクリプト)** コンポーネントをすべてのオブジェクトに追加します。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> このチュートリアルでは、colliders が既に prefabs に追加されています。 キューブオブジェクトなどの Unity プリミティブの場合、オブジェクトの作成時に Collider コンポーネントが自動的に追加されます。 上の図では、colliders は緑色のアウトラインで表されています。 Colliders の詳細については、Unity の<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a>のドキュメントを参照してください。

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2. Near の相互作用 Grabbable (スクリプト) コンポーネントを prefab オブジェクトに追加する

階層 ウィンドウで、**チーズ** オブジェクトを選択し、 **shift**キーを押したまま、**モジュール** オブジェクトを選択し、 **Near インタラクション Grabbable (スクリプト)** コンポーネントをすべてのオブジェクトに追加します。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3. 操作ハンドラー (スクリプト) コンポーネントを構成する

#### <a name="default-manipulation"></a>既定の操作

既定の操作動作を実行するには、**キューブ**オブジェクトに対して、すべてのプロパティを既定のままにします。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> コンポーネントを既定値にリセットするには、コンポーネントの設定アイコンを選択し、[リセット] を選択します。

#### <a name="restrict-manipulation-to-scale-only"></a>操作をスケールのみに制限する

**Cube (1)** オブジェクトの場合は、 **2 つのきき操作の種類**を**Scale**に変更し、ユーザーがオブジェクトのサイズを変更できるようにします。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>ユーザーからの固定距離への移動を制限する

**Cube (2)** オブジェクトの場合は、移動時**に制約**を変更して、オブジェクトが移動されたときに、ユーザーからの距離を維持した**ままにし**ます。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>既定の grabbable 操作

**チーズ**、 **CoffeCup**、および**EarthCore**オブジェクトの場合は、既定ですべてのプロパティをそのままにして、既定の grabbable 操作動作を体験します。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>遠くの操作の機能を削除する

**Octa**オブジェクトの場合は、[ **Far 操作を許可**する] チェックボックスをオフにして、ユーザーが追跡したハンドを使用して直接オブジェクトと対話できるようにします。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>オブジェクトを中央に回転させる

**プラトニック**オブジェクトの場合は、一方の**手の回転モードの近く**と1つの手回転モードを**遠く**に**回転させ**ます。これにより、ユーザーがオブジェクトを1つ回転させると、オブジェクトの中心を中心に回転します。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a>オブジェクトがリリースされた後も移動を続ける

**モジュール**オブジェクトの場合は、 **Rigidbody**コンポーネントを追加して物理を有効にします。次に、オブジェクトが重力の影響を受けないように、[**重力を使用**する] チェックボックスをオフにします。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

操作ハンドラー (スクリプト) コンポーネントに戻り、**リリースの動作**が [**ベロシティを維持**する] に設定されていることを確認し、オブジェクトがユーザーから解放された後も移動し続けるようにします。

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

操作ハンドラーコンポーネントとそれに関連付けられているプロパティの詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[操作ハンドラー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)ガイドを参照してください。

## <a name="adding-bounding-boxes"></a>境界ボックスの追加

境界ボックスを使用すると、拡大縮小および回転に使用できるハンドルを提供することによって、近距離および遠くの相互作用のために、オブジェクトを簡単かつ直感的に操作できるようになります。

この例では、EarthCore オブジェクトに境界ボックスを追加します。これにより、前のセクションで構成したオブジェクト操作を使用して、境界ボックスハンドルを使用してスケールおよび回転することで、このオブジェクトと対話できるようになります。

> [!IMPORTANT]
> **境界ボックス**を使用できるようにするには、オブジェクトに次のコンポーネントが必要です。
>
> * **Collider**コンポーネント (Box collider など)
> * **境界ボックス (スクリプト)** コンポーネント

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1. 境界ボックス (スクリプト) コンポーネントを EarthCore オブジェクトに追加する

[インスペクター] ウィンドウで、 **EarthCore**オブジェクトを選択し、**境界ボックス (スクリプト)** コンポーネントを EarthCore オブジェクトに追加します。

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> 境界ボックスの視覚エフェクトは実行時に作成されるため、ゲームモードに入る前には表示されません。

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2. エディター内シミュレーションを使用して境界ボックスを視覚化およびテストする

再生ボタンを押してゲームモードに入ります。 次に、space キーを押して手を置き、マウスを使用して境界ボックスと対話します。

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

境界ボックスコンポーネントとそれに関連付けられているプロパティの詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[境界ボックス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)ガイドを参照してください。

## <a name="adding-touch-effects"></a>タッチ効果の追加

この例では、手の形でオブジェクトを操作したときにイベントがトリガーされるようにします。 具体的には、ユーザーが操作したときにサウンド効果を再生するように、Octa オブジェクトを構成します。

これを実現するには、主に次の手順を実行します。

1. オーディオソースコンポーネントをオブジェクトに追加する
2. Near 相互作用 Touchable (スクリプト) コンポーネントをオブジェクトに追加します。
3. オブジェクトにハンドインタラクションタッチ (スクリプト) コンポーネントを追加します。
4. タッチ開始イベントを実装する
5. エディター内シミュレーションを使用したタッチ操作のテスト

> [!IMPORTANT]
> **タッチイベントをトリガー**できるようにするには、オブジェクトに次のコンポーネントが必要です。
>
> * **Collider**コンポーネント (可能であれば Box Collider)
> * **Near 相互作用 Touchable (スクリプト)** コンポーネント
> * **ハンドインタラクションタッチ (スクリプト)** コンポーネント

> [!NOTE]
> 手書き操作タッチ (スクリプト) コンポーネントは、MRTK の一部ではありません。 このチュートリアルのアセットと共にインポートされ、もともとは MixedReality Toolkit Unity の例に含まれています。

### <a name="1-add-an-audio-source-component-to-the-object"></a>1. オーディオソースコンポーネントをオブジェクトに追加する

[階層] ウィンドウで、 **Octa**オブジェクトを選択し、**オーディオソース**コンポーネントを octa オブジェクトに追加します。次に、空間**ブレンド**を1に変更して、空間オーディオを有効にします。

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2. Near 相互作用 Touchable (スクリプト) コンポーネントをオブジェクトに追加します。

**Octa**オブジェクトを選択した状態で、 **Touchable (スクリプト)** コンポーネントを octa オブジェクトに追加します。次に、 **[境界の修正]** と センターの **[修正]** ボタンをクリックして、Near 相互作用 Touchable (スクリプト) のローカルの中央および境界のプロパティを boxcollider と一致するように更新します。

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3. ハンドインタラクションタッチ (スクリプト) コンポーネントをオブジェクトに追加する

**Octa**オブジェクトを選択した状態で、次のように、**手動インタラクションタッチ (スクリプト)** コンポーネントを octa オブジェクトに追加します。

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4. タッチ開始イベントを実装する

手書き入力**タッチ (スクリプト)** コンポーネントで、小さい **+** アイコンをクリックし**て、タッチ開始 ()** イベントの新しいイベントを作成します。 次に、イベントを受信するように**Octa**オブジェクトを構成し、トリガーされるアクションとして**PlayOneShot**を定義します。

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

**[アセット]**  > [ **> > ]** に移動して、mrtk で提供されているオーディオクリップを表示し、適切なオーディオクリップを**オーディオクリップ**フィールド (たとえば、MRTK_Gem オーディオクリップ) に**割り当てます。**

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> イベントの実装方法に関する注意事項については、「[ハンドトラッキングジェスチャ」と「対話型 buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 」を参照してください。

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5. エディター内のシミュレーションを使用してタッチ操作をテストする

再生ボタンを押してゲームモードに入ります。 次に、space キーを押して手を置き、マウスを使用して Octa オブジェクトにタッチし、サウンド効果をトリガーします。

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> タッチ操作のテスト時に見たように、上の図に示すように、処理されたときに、Octa オブジェクトの色が表示されます。 この効果は、前述の手順で完了したイベント構成の結果ではなく、ハンドインタラクションタッチ (スクリプト) コンポーネントにハードコーディングされます。
>
> この効果を無効にする場合は、たとえばコメントアウトまたは行 32 ' TargetRenderer = GetComponentInChildren<Renderer>(); ' を指定すると、TargetRenderer が null になり、色はません。

## <a name="congratulations"></a>結論

このチュートリアルでは、グリッドコレクション内の3D オブジェクトを整理する方法と、近くの操作 (追跡したハンドを使用した直接グラブ) と遠くの相互作用 (宝石を使用した、または光線を使用) を使用して、これらのオブジェクトを操作する方法について学習しました。 また、3D オブジェクトの周囲に境界ボックスを配置する方法と、境界ボックスでハンドルを使用およびカスタマイズする方法についても学習しました。 最後に、オブジェクトにタッチしたときにイベントをトリガーする方法を学習しました。

[次のレッスン: 6. 詳細な入力オプションの調査](mrlearning-base-ch5.md)
