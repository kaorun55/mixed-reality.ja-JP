---
title: 入門チュートリアル-6. 詳細な入力オプションの調査
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: aaa02ce118fd051d94311e837b143affc96ff72b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554256"
---
# <a name="6-exploring-advanced-input-options"></a>6. 詳細な入力オプションを調査する

このチュートリアルでは、HoloLens 2 の高度な入力オプションをいくつか紹介します。これには、音声コマンド、パンジェスチャ、および視線追跡の使用が含まれます。

## <a name="objectives"></a>目標

* 音声コマンドとキーワードを使用してイベントをトリガーする
* 追跡したハンドを使用して、追跡したハンドでテクスチャと3D オブジェクトをパンする
* HoloLens 2 の監視機能を活用してオブジェクトを選択する

## <a name="enabling-voice-commands"></a>音声コマンドの有効化
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

このセクションでは、speech コマンドを実装して、ユーザーが Octa オブジェクトでサウンドを再生できるようにします。 このためには、新しい speech コマンドを作成し、speech コマンドキーワードが話されたときに目的のアクションをトリガーするようにイベントを構成します。

これを実現するには、主に次の手順を実行します。

1. 既定の入力システムプロファイルを複製する
2. 既定の Speech コマンドプロファイルを複製する
3. 新しい speech コマンドを作成する
4. 音声入力ハンドラー (スクリプト) コンポーネントを追加して構成する
5. Speech コマンドの応答イベントを実装します。

### <a name="1-clone-the-default-input-system-profile"></a>1. 既定の入力システムプロファイルを複製します。

階層 ウィンドウで**MixedRealityToolkit**オブジェクトを選択し、インスペクター ウィンドウで **入力** タブを選択し、 **DefaultHoloLens2InputSystemProfile**を複製して独自のカスタマイズ可能な**入力システムプロファイル**に置き換えます。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> MRTK プロファイルの複製方法に関する注意事項については、「 [Mixed Reality Toolkit プロファイルの構成方法](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)」を参照してください。

### <a name="2-clone-the-default-speech-commands-profile"></a>2. 既定の Speech コマンドプロファイルを複製します。

**Speech**セクションを展開し、 **DefaultMixedRealitySpeechCommandsProfile**を複製して、カスタマイズ可能な独自の**Speech コマンドプロファイル**に置き換えます。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3. 新しい speech コマンドを作成する

**[音声コマンド]** セクションで、 **[+ 新しい音声]** コマンドの追加 ボタンをクリックして、既存の音声コマンドの一覧の一番下に新しい speech コマンドを追加します。次に、 **[キーワード]** フィールドに適切な単語または語句を入力します。たとえば、 **[音楽の再生]** を選択します。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> コンピューターにマイクが搭載されていない場合に、エディター内のシミュレーションを使用して音声コマンドをテストするには、キーコードを speech コマンドに割り当てることができます。これにより、対応するキーが押されたときに、トリガーを起動することができます。

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4. 音声入力ハンドラー (スクリプト) コンポーネントを追加して構成する

[階層] ウィンドウで、 **Octa**オブジェクトを選択し、 **Speech 入力ハンドラー (スクリプト)** コンポーネントを octa オブジェクトに追加します。 次に、 **[フォーカスが必要]** チェックボックスをオフにして、ユーザーが speech コマンドをトリガーするために octa オブジェクトを確認する必要がないようにします。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5. speech コマンドの応答イベントを実装する

[音声入力ハンドラー (スクリプト)] コンポーネントで、[小さい **+** ] ボタンをクリックし、キーワードの一覧にキーワード要素を追加します。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

新しく作成した**要素 0**をクリックして展開し、 **[キーワード]** ドロップダウンから、前の手順で作成した**Play Music**キーワードを選択します。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> キーワードドロップダウンのキーワードは、Speech コマンドのプロファイルにある音声コマンドリストで定義されているキーワードに基づいて設定されます。

新しい**Response ()** イベントを作成し、イベントを受信するように**octa**オブジェクトを構成し、トリガーするアクションとして**PlayOneShot**を定義し **、オーディオクリップフィールドに**適切なオーディオクリップ (たとえば、MRTK_Gem オーディオクリップ) を割り当てます。

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> イベントの実装方法とオーディオクリップの割り当て方法に関する注意事項については、「[タッチ開始イベントの実装](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event)」を参照してください。

## <a name="the-pan-gesture"></a>パン ジェスチャ

パンジェスチャは、指またはハンドを使用してコンテンツをスクロールすることでスクロールする場合に便利です。 この例では、まず 2D UI をスクロールし、それを展開して、3D オブジェクトのコレクションをスクロールできるようにする方法について説明します。

これを実現するには、主に次の手順を実行します。

1. パンに使用できるクワッドオブジェクトを作成する
2. Near 相互作用 Touchable (スクリプト) コンポーネントを追加します。
3. ハンドインタラクションのパンズーム (スクリプト) コンポーネントを追加する
4. スクロールする2D コンテンツを追加する
5. スクロールする3D コンテンツを追加する
6. Move With Pan (スクリプト) コンポーネントを追加する

> [!NOTE]
> Move With Pan (スクリプト) コンポーネントは、MRTK の一部ではありません。 このチュートリアルでは、このチュートリアルのアセットを提供しました。

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1. パンに使用できるクワッドオブジェクトを作成する

[階層] ウィンドウで、空の領域を右クリックし、[ **3D オブジェクト** > **クワッド**] を選択して、四角形をシーンに追加します。 適切な名前 (たとえば、「 **Pangesture**) を指定し、適切な場所に配置します (例: X = 0、Y =-0.2、Z = 2)。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> 3D quad などの Unity プリミティブをシーンに追加する方法については、「[キューブをシーンに追加](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene)する」の説明を参照してください。

他の対話と同様に、パンジェスチャにも collider が必要です。 既定では、クワッドにはメッシュ collider があります。 ただし、メッシュ collider は非常に薄いため、理想的ではありません。 ユーザーが collider との対話を容易にするために、メッシュ collider を box collider に置き換えます。

PanGesture が選択された状態で、**メッシュ collider**コンポーネントの**設定**アイコンをクリックし、 **[コンポーネントの削除]** を選択してメッシュ Collider を削除します。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

インスペクター ウィンドウで、**コンポーネントの追加** ボタンを使用して**box collider**を追加し、box の collider **Size** Z を0.15 に変更して box collider の太さを増やします。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2. Near 相互作用 Touchable (スクリプト) コンポーネントを追加します。

**Pangesture**オブジェクトが選択された状態で、 **Near 相互作用 Touchable (スクリプト)** コンポーネントを pangesture に追加します。次に、 **[境界の修正]** と センターの **[修正]** ボタンをクリックして、Near 相互作用 Touchable (スクリプト) のローカルの中心と境界のプロパティを boxcollider と一致するように更新します。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3. ハンドインタラクションのパンズーム (スクリプト) コンポーネントを追加する

**Pangesture**オブジェクトが選択された状態で、**ハンドインタラクションのパンズーム (スクリプト)** コンポーネントを pangesture に追加し、[**水平**方向にロック] チェックボックスをオンにして垂直スクロールのみを許可します。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4. スクロールする2D コンテンツを追加する

[プロジェクト] パネルで、 **Pancontent**の素材を検索し、[-] をクリックして、 **Pangesture**オブジェクトのメッシュレンダラー**マテリアル**0 プロパティにドラッグします。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

[インスペクター] ウィンドウで、新しく追加した**Pancontent**マテリアルコンポーネントを展開し、 **[タイル]** の Y 値を0.5 に変更します。これにより X 値が一致し、タイルが正方形で表示されます。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

ここでゲームモードに入ると、エディター内のシミュレーションでパンジェスチャを使用して、2D コンテンツのスクロールをテストできます。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5. スクロールする3D コンテンツを追加する

[階層] ウィンドウで、 **Pangesture**オブジェクトの子オブジェクトとして**4 つのキューブを作成**し、その変換の**スケール**を X = 0.15、Y = 0.15、Z = 0.15 に設定します。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

キューブの間隔を均等にし、時間を節約するには、 **Grid オブジェクトコレクション (スクリプト)** コンポーネントをキューブの親オブジェクト (つまり、 **pangesture** ) に追加し、次のようにグリッドオブジェクトコレクション (スクリプト) を構成します。

* すべてのキューブが1つの行にアラインメントされるようにするには、 **Num Rows**を1に変更します。
* **セルの幅**を0.25 に変更して、行内のキューブを空白にします。

次に、 **[コレクションの更新]** ボタンをクリックして、新しい構成を適用します。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6. Pan (スクリプト) コンポーネントでの移動を追加する

階層 ウィンドウで、すべての**キューブ子オブジェクト**を選択します。次に、インスペクター ウィンドウで **コンポーネントの追加** ボタンを使用して、 **Move With Pan (スクリプト)** コンポーネントをすべてのキューブに追加します。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> [階層] ウィンドウで複数のオブジェクトを選択する方法に関する注意事項については、「[操作ハンドラーを追加する (スクリプト) コンポーネントをすべてのオブジェクトの命令に追加](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)する」を参照してください。

すべてのキューブが選択された状態で、 **Pangesture**をクリックして、 **[パン入力ソース]** フィールドにドラッグします。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> 各キューブの [Move With Pan (スクリプト)] コンポーネントでは、前の手順で [パン] 入力ソースとして割り当てた PanGesture の [Paninteractionpanzoom (スクリプト)] コンポーネントによって送信されたパン更新イベントをリッスンし、各キューブの位置を更新します。適切.

階層 ウィンドウで、 **Pangesture**オブジェクトを選択し、インスペクター で**メッシュレンダラー**の**チェック**ボックスをオフにして、メッシュレンダラーコンポーネントを無効にします。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

ゲームモードに入ると、エディター内のシミュレーションでパンジェスチャを使用して、3D コンテンツのスクロールをテストできます。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>視線追跡

このセクションでは、プロジェクトでアイトラッキングを有効にする方法について説明します。 この例では、ユーザーの視点で見ている間に、3DObjectCollection の各オブジェクトの回転速度を低下させる機能を実装します。また、参照しているオブジェクトがエアタップまたは音声コマンドによって選択されたときにブリップが発生効果をトリガーします。

これを実現するには、主に次の手順を実行します。

1. すべての対象オブジェクトにアイ Tracking ターゲット (スクリプト) コンポーネントを追加する
2. すべてのターゲットオブジェクトにアイトラッキングチュートリアルのデモ (スクリプト) コンポーネントを追加する
3. ターゲットイベントの参照中にを実装します
4. 選択したイベントにを実装します
5. エディター内のシミュレーションのシミュレートされた目の追跡を有効にする
6. Visual Studio プロジェクトのアプリ機能での、宝石による入力を有効にする

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1. すべてのターゲットオブジェクトにアイ Tracking ターゲット (スクリプト) コンポーネントを追加します。

階層 ウィンドウで、 **3DObjectCollection**オブジェクトを展開し、すべての**子オブジェクト**を選択します。次に、インスペクター ウィンドウで **コンポーネントの追加** ボタンを使用して、すべての子オブジェクトに**視線追跡ターゲット (スクリプト)** コンポーネントを追加します。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

すべての**子オブジェクト**が選択された状態で、次のように**視線追跡ターゲット (スクリプト)** コンポーネントを構成します。

* 選択**操作**の選択を変更**し、この**オブジェクトのエアタップアクションを select として定義します
* **[音声の選択]** を展開し、[音声コマンド一覧の**サイズ**] を1に設定します。次に、表示される新しい要素の一覧で、[**要素 0** **] を [選択**] に変更し、このオブジェクトの音声コマンドアクションを [選択] として定義します。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2. すべてのターゲットオブジェクトにアイトラッキングチュートリアルのデモ (スクリプト) コンポーネントを追加する

すべての**子オブジェクト**がまだ選択されている状態で、 **[コンポーネントの追加]** ボタンを使用して、すべての子オブジェクトに**アイトラッキングチュートリアルのデモ (スクリプト)** コンポーネントを追加します。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> アイ Tracking のターゲット (スクリプト) コンポーネントは、MRTK の一部ではありません。 このチュートリアルでは、このチュートリアルのアセットを提供しました。

### <a name="3-implement-the-while-looking-at-target-event"></a>3. ターゲットイベントの参照中にを実装します。

階層 ウィンドウで、**チーズ** オブジェクトを選択し、 **Target ()** イベントを参照して新しいを作成します。次に、イベントを受信するように**チーズ**オブジェクトを構成し、トリガーするアクションとして**EyeTrackingTutorialDemo**を定義します。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

3DObjectCollection 内の各子オブジェクトに対して、この**手順を繰り返し**ます。

> [!TIP]
> イベントの実装方法に関する注意事項については、「[ハンドトラッキングジェスチャ」と「対話型 buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 」を参照してください。

### <a name="4-implement-the-on-selected-event"></a>4. 選択したイベントにを実装する

階層 ウィンドウで、**チーズ** オブジェクトを選択し、**選択された**イベントを新規に作成 () イベントを作成します。次に、イベントを受信するように**チーズ**オブジェクトを構成し、トリガーされるアクションとして**EyeTrackingTutorialDemo**を定義します。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

3DObjectCollection 内の各子オブジェクトに対して、この**手順を繰り返し**ます。

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5. エディター内のシミュレーションのシミュレートされた目の追跡を有効にする

階層] ウィンドウで **[MixedRealityToolkit]** オブジェクトを選択し、[インスペクター ウィンドウで [入力 **] タブ**を選択します。次に、入力 **[データプロバイダー]** セクションを展開し、 **[入力シミュレーションサービス]** セクションを展開し、 **DefaultMixedRealityInputSimulationProfile**を複製して独自のカスタマイズ可能な**入力シミュレーションプロファイル**に置き換えます。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> MRTK プロファイルの複製方法に関する注意事項については、「 [Mixed Reality Toolkit プロファイルの構成方法](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)」を参照してください。

**[目のシミュレーション]** セクションで、目の **[位置をシミュレート]** する チェックボックスをオンにして、視線追跡シミュレーションを有効にします。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

ゲームモードに入ると、次のようにビューを調整することで、実装したスピンとブリップが発生の効果をテストできます。これにより、カーソルがオブジェクトの1つにヒットし、手動操作または音声コマンドを使用してオブジェクトを選択できるようになります。

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> DefaultHoloLens2ConfigurationProfile を使用してカスタマイズ可能な MRTK 構成プロファイルを複製しなかった場合は、「 [Mixed Reality Toolkit の構成](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)」の手順で説明したように、プロジェクトで目の追跡が有効にならないため、有効にする必要があります。 詳細については、「 [MRTK の監視](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)の概要」の手順を参照してください。

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6. Visual Studio プロジェクトのアプリ機能で、入力を見つめて有効にする

アプリをビルドして、Visual Studio からデバイスにデプロイする前に、プロジェクトのアプリの機能で、お客様のアプリの入力が有効になっている必要があります。 これには、 [HoloLens 2 命令での Unity アプリのテスト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)に従うことができます。

## <a name="congratulations"></a>結論

これで、アプリケーションに基本的な監視機能が追加されました。 これらの操作は、視線追跡が持つ可能性のほんの一部にすぎません。 このチュートリアルでは、音声コマンドやパンジェスチャなど、その他の高度な入力機能についても学習しました。

[次のレッスン: 7. 旧暦モジュールサンプルアプリケーションの作成](mrlearning-base-ch6.md)
