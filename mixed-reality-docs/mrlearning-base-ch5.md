---
title: 入門チュートリアル - 6. 高度な入力オプションの探索
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: ec078015304e1cddc9b042fb5e94cf1904a302cb
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376089"
---
# <a name="6-exploring-advanced-input-options"></a>6.高度な入力オプションの探索

このチュートリアルでは、音声コマンド、パン ジェスチャ、視線追跡などを含む、HoloLens 2 でのいくつかの高度な入力オプションについて学習します。

## <a name="objectives"></a>目標

* 音声コマンドとキーワードを使用してイベントをトリガーする
* 追跡対象の手を使用してテクスチャと 3D オブジェクトをパンする
* HoloLens 2 の視線追跡機能を活用してオブジェクトを選択する

## <a name="enabling-voice-commands"></a>音声コマンドの有効化
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

このセクションでは、音声コマンドを実装して、ユーザーが Octa オブジェクトでサウンドを再生できるようにします。 このためには、新しい音声コマンドを作成し、音声コマンドのキーワードが発話されたときに目的のアクションをトリガーするようにイベントを構成します。

これを実現するための主な手順は次のとおりです。

1. 既定の入力システム プロファイルを複製する
2. 既定の音声コマンド プロファイルを複製する
3. 新しい音声コマンドを作成する
4. Speech Input Handler (Script) コンポーネントを追加して構成する
5. 音声コマンドの Response イベントを実装する

### <a name="1-clone-the-default-input-system-profile"></a>1.既定の入力システム プロファイルを複製する

[Hierarchy]\(階層\) ウィンドウで **[MixedRealityToolkit]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **[Input]\(入力\)** タブを選択し、 **[DefaultHoloLens2InputSystemProfile]** を複製して、カスタマイズ可能な独自の**入力システム プロファイル**に置き換えます。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> MRTK プロファイルを複製する方法については、[Mixed Reality Toolkit プロファイルを構成する方法](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)に関する説明を参照してください。

### <a name="2-clone-the-default-speech-commands-profile"></a>2.既定の音声コマンド プロファイルを複製する

**[Speech]\(音声\)** セクションを展開し、 **[DefaultMixedRealitySpeechCommandsProfile]** を複製して、カスタマイズ可能な独自の**音声コマンド プロファイル**に置き換えます。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3.新しい音声コマンドを作成する

**[Speech Commands]\(音声コマンド\)** セクションで、 **[+Add a New Speech Command]\(新しい音声コマンドの追加\)** ボタンをクリックして、既存の音声コマンドの一覧の一番下に新しい音声コマンドを追加します。次に、 **[Keyword]\(キーワード\)** フィールドに適切な単語または語句 (たとえば、**Play Music**) を入力します。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> コンピューターにマイクがない場合に、エディター内のシミュレーションを使用して音声コマンドをテストするには、キーコードを音声コマンドに割り当て、対応するキーが押されたときにそれをトリガーすることができます。

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4.Speech Input Handler (Script) コンポーネントを追加して構成する

[Hierarchy]\(階層\) ウィンドウで、 **[Octa]** オブジェクトを選択し、**Speech Input Handler (Script)** コンポーネントを Octa オブジェクトに追加します。 次に、 **[Is Focus Required]\(フォーカスが必要\)** チェックボックスをオフにして、ユーザーが Octa オブジェクトを確認しなくても音声コマンドをトリガーできるようにします。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5.音声コマンドの Response イベントを実装する

Speech Input Handler (Script) コンポーネントで、小さい **+** ボタンをクリックして、キーワードの一覧にキーワード要素を追加します。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

新しく作成した **[Element 0]\(要素 0\)** をクリックして展開し、 **[Keyword]\(キーワード\)** ドロップダウンから、前に作成した **[Play Music]** キーワードを選択します。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> [Keyword]\(キーワード\) ドロップダウンのキーワードは、音声コマンド プロファイルにある音声コマンド リストで定義されているキーワードに基づいて設定されます。

新しい **Response ()** イベントを作成し、イベントを受信するように **Octa** オブジェクトを構成し、トリガーするアクションとして **AudioSource.PlayOneShot** を定義します。次に、適切なオーディオ クリップ (MRTK_Gem オーディオ クリップなど) を **[Audio Clip]\(オーディオ クリップ\)** フィールドに割り当てます。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> イベントを実装してオーディオ クリップを割り当てる方法については、「[On Touch Started イベントを実装する](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event)」の説明を参照してください。

## <a name="the-pan-gesture"></a>パン ジェスチャ

パン ジェスチャは、指または手を使ってコンテンツをスクロールするのに役立ちます。 この例では、まず 2D UI をスクロールし、次にそれを展開して 3D オブジェクトのコレクションをスクロールできるようにする方法について説明します。

これを実現するための主な手順は次のとおりです。

1. パンに使用できる Quad オブジェクトを作成する
2. Near Interaction Touchable (Script) コンポーネントを追加する
3. Hand Interaction Pan Zoom (Script) コンポーネントを追加する
4. スクロールする 2D コンテンツを追加する
5. スクロールする 3D コンテンツを追加する
6. Move With Pan (Script) コンポーネントを追加する

> [!NOTE]
> Move With Pan (Script) コンポーネントは、MRTK の一部ではありません。 このチュートリアルのアセットと共に提供されました。

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1.パンに使用できる Quad オブジェクトを作成する

[Hierarchy]\(階層\) ウィンドウで、空の領域を右クリックし、 **[3D Object]\(3D オブジェクト\)**  >  **[Quad]** を選択して、Quad をシーンに追加します。 **PanGesture** のような適切な名前を付け、適切な場所に配置します (たとえば、X = 0、Y = - 0.2、Z = 2 など)。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> Unity プリミティブ (3D quad など) をシーンに追加する方法については、「[キューブをシーンに追加する](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene)」の説明を参照してください。

他の操作と同様に、パン ジェスチャにもコライダーが必要です。 既定では、Quad にはメッシュ コライダーがあります。 ただし、メッシュ コライダーは極めて薄いため、理想的ではありません。 ユーザーがコライダーを簡単に操作できるようにするために、メッシュ コライダーをボックス コライダーに置き換えます。

PanGesture オブジェクトを選択した状態で、**Mesh Collider** コンポーネントの **[Settings]\(設定\)** アイコンをクリックし、 **[Remove Component]\(コンポーネントの削除\)** を選択してメッシュ コライダーを削除します。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンを使用して**ボックス コライダー**を追加し、ボックス コライダーの **[Size]\(サイズ\)** Z を 0.15 に変更してボックス コライダーの厚みを増やします。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2.Near Interaction Touchable (Script) コンポーネントを追加する

**[PanGesture]** オブジェクトが選択された状態で、**Near Interaction Touchable (Script)** コンポーネントを PanGesture オブジェクトに追加します。次に、 **[Fix Bounds]\(境界の修正\)** および **[Fix Center]\(センターの修正\)** ボタンをクリックして、Near Interaction Touchable (Script) の [Local Center]\(ローカルのセンター\) および [Bounds]\(境界\) のプロパティを BoxCollider に一致するように更新します。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3.Hand Interaction Pan Zoom (Script) コンポーネントを追加する

**PanGesture** オブジェクトが選択された状態で、**Hand Interaction Pan Zoom (Script)** コンポーネントを PanGesture オブジェクトに追加し、次に **[Lock Horizontal]\(水平方向のロック\)** チェックボックスをオンにして、垂直スクロールのみを許可します。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4.スクロールする 2D コンテンツを追加する

[Project]\(プロジェクト\) パネルで **PanContent** 素材を検索し、それをクリックして **PanGesture** オブジェクトのメッシュ レンダラー **[Materials]\(素材\)** の [Element 0]\(要素 0\) プロパティにドラッグします。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

[Inspector]\(インスペクター\) ウィンドウで、新しく追加した **PanContent** 素材コンポーネントを展開します。次に、 **[Tiling]\(タイル表示\)** の Y 値を 0.5 に変更して X 値と一致させ、タイルを正方形で表示します。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

ここでゲーム モードに入ると、エディター内のシミュレーションでパン ジェスチャを使用して、2D コンテンツのスクロールをテストできます。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5.スクロールする 3D コンテンツを追加する

[Hierarchy]\(階層\) ウィンドウで、**PanGesture** オブジェクトの子オブジェクトとして **4 つのキューブを作成し**、[Transform]\(変換\) の **[Scale]\(スケール\)** を X = 0.15、Y = 0.15、Z = 0.15 に設定します。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

キューブを均等に配置して時間を節約するには、**Grid Object Collection (Script)** コンポーネントをキューブの親オブジェクト (**PanGesture** オブジェクト) に追加し、次のようにグリッド オブジェクト コレクション (スクリプト) を構成します。

* **[Num Rows]\(行数\)** を 1 に変更して、すべてのキューブを 1 行に整列させる
* **[Cell Width]\(セル幅\)** を 0.25 に変更して、行内でキューブを一定間隔で並べる

次に、**Update Collection｣\(コレクションの更新\)** ボタンをクリックして、新しい構成を適用します。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6.Move With Pan (Script) コンポーネントを追加する

[Hierarchy]\(階層\) ウィンドウで、すべての**キューブ子オブジェクト**を選択してから、[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Move With Pan (Script)** コンポーネントをすべてのキューブに追加します。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> [Hierarchy]\(階層\) ウィンドウで複数のオブジェクトを選択する方法については、[すべてのオブジェクトに Manipulation Handler (Script) コンポーネントを追加する](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)方法に関する説明 を参照してください。

すべてのキューブが選択された状態で、**PanGesture** オブジェクトをクリックし、 **[Pan Input Source]\(パン入力ソース\)** フィールドにドラッグします。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> 各キューブの Move With Pan (Script) コンポーネントでは、前の手順でパン入力ソースとして割り当てた PanGesture オブジェクトの HandInteractionPanZoom (Script) コンポーネントによって送信される Pan Updated イベントをリッスンし、それに従って各キューブの位置を更新します。

[Hierarchy]\(階層\) ウィンドウで **[PanGesture]** オブジェクトを選択し、次にインスペクターで **[Mesh Renderer]\(メッシュ レンダラー\)** チェックボックスを**オフにして**、Mesh Renderer コンポーネントを無効にします。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

ここでゲーム モードに入ると、エディター内のシミュレーションでパン ジェスチャを使用して、3D コンテンツのスクロールをテストできます。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>視線追跡

このセクションでは、プロジェクトで視線追跡を有効にする方法を学習します。 この例では、ユーザーが視線を向けている間、3DObjectCollection の各オブジェクトをゆっくり回転させるとともに、視線を向けているオブジェクトがエアタップまたは音声コマンドによって選択されたときにブリップ効果をトリガーする機能を実装します。

これを実現するための主な手順は次のとおりです。

1. Eye Tracking Target (Script) コンポーネントをすべてのターゲット オブジェクトに追加する
2. Eye Tracking Tutorial Demo (Script) コンポーネントをすべてのターゲット オブジェクトに追加する
3. While Looking At Target イベントを実装する
4. On Selected イベントを実装する
5. エディター内のシミュレーションでシミュレートされた視線追跡を有効にする
6. Visual Studio プロジェクトのアプリ機能で視線入力を有効にする

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1.Eye Tracking Target (Script) コンポーネントをすべてのターゲット オブジェクトに追加する

[Hierarchy]\(階層\) ウィンドウで、 **[3DObjectCollection]** オブジェクトを展開し、すべての**子オブジェクト**を選択してから、[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Eye Tracking Target (Script)** コンポーネントをすべての子オブジェクトに追加します。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

すべての**子オブジェクト**が選択された状態で、**Eye Tracking Target (Script)** コンポーネントを次のように構成します。

* **[Select Action]\(アクションの選択\)** を **[Select]\(選択\)** に変更して、このオブジェクトのエアタップ アクションを [Select]\(選択\) として定義します
* **[Voice Select]\(音声の選択\)** を展開し、音声コマンドの一覧の **[Size]\(サイズ\)** を 1 に設定し、表示される新しい要素の一覧で、 **[Element 0]\(要素 0\)** を **[Select]\(選択)** に変更して、このオブジェクトの音声コマンド アクションを [Select]\(選択) として定義します

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2.Eye Tracking Tutorial Demo (Script) コンポーネントをすべてのターゲット オブジェクトに追加する

すべての**子オブジェクト**が選択された状態で、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Eye Tracking Tutorial Demo (Script)** コンポーネントをすべての子オブジェクトに追加します。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> Eye Tracking Target (Script) コンポーネントは、MRTK の一部ではありません。 このチュートリアルのアセットと共に提供されました。

### <a name="3-implement-the-while-looking-at-target-event"></a>3.While Looking At Target イベントを実装する

[Hierarchy]\(階層\) ウィンドウで **[Cheese]** オブジェクトを選択してから、新しい **While Looking At Target ()** イベントを作成し、イベントを受信するように **[Cheese]** オブジェクトを構成し、トリガーされるアクションとして **EyeTrackingTutorialDemo.RotateTarget** を定義します。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

3DObjectCollection 内のそれぞれの子オブジェクトに対して**繰り返します**。

> [!TIP]
> イベントを実装する方法については、「[手の追跡のジェスチャと操作可能なボタン](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)」の説明を参照してください。

### <a name="4-implement-the-on-selected-event"></a>4.On Selected イベントを実装する

[Hierarchy]\(階層\) ウィンドウで **[Cheese]** オブジェクトを選択し、新しい **On Selected ()** イベントを作成します。次に、イベントを受信するように **[Cheese]** オブジェクトを構成し、トリガーするアクションとして **EyeTrackingTutorialDemo.BlipTarget** を定義します。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

3DObjectCollection 内のそれぞれの子オブジェクトに対して**繰り返します**。

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5.エディター内のシミュレーションでシミュレートされた視線追跡を有効にする

[Hierarchy]\(階層\) ウィンドウで **[MixedRealityToolkit]** オブジェクトを選択し、次に [Inspector]\(インスペクター\) ウィンドウで **[Input]\(入力\)** タブを選択し、 **[Input Data Providers]\(入力データ プロバイダー)\** セクションを展開して、 **[Input Simulation Service]\(入力シミュレーション サービス\)** セクションを展開し、**DefaultMixedRealityInputSimulationProfile** を複製して、カスタマイズ可能な独自の **[Input Simulation Profile]\(入力シミュレーション プロファイル\)** に置き換えます。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> MRTK プロファイルを複製する方法については、[Mixed Reality Toolkit プロファイルを構成する方法](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)に関する説明を参照してください。

**[Eye Simulation]\(目のシミュレーション\)** セクションで、 **[Simulate Eye Position]\(目の位置のシミュレート\)** チェックボックスをオンにし て、視線追跡シミュレーションを有効にします。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

ここでゲーム モードに入ると、カーソルがオブジェクトの 1 つに接触するようにビューを調整し、手の操作または音声コマンドを使用してオブジェクトを選択することによって、実装したスピンとブリップの効果をテストできます。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> 「[Mixed Reality ツールキットを構成する](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)」の手順に従って、DefaultHoloLens2ConfigurationProfile を使用して、カスタマイズ可能な MRTK 構成プロファイルを複製しなかった場合、視線追跡がプロジェクトで有効になっていない場合があり、有効にする必要があります。 詳細については、「[MRTK での視線追跡の概要](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)」 の手順を参照してください。

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6.Visual Studio プロジェクトのアプリ機能で視線入力を有効にする

アプリをビルドして、Visual Studio からお使いのデバイスにデプロイする前に、プロジェクトのアプリの機能で視線入力が有効になっている必要があります。 そのためには、 [HoloLens 2 の Unity アプリのテスト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)に関するページの手順を使用できます。

## <a name="congratulations"></a>結論

これで基本的な視線追跡機能をアプリケーションに追加することができました。 これらの操作は、視線追跡が持つ可能性のほんの一部にすぎません。 このチュートリアルでは、音声コマンドやパン ジェスチャなど、その他の高度な入力機能についても学習しました。

[次のレッスン:7.月着陸船サンプル アプリケーションの作成](mrlearning-base-ch6.md)
