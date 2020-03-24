---
title: 入門チュートリアル - 7. 月着陸船サンプル アプリケーションの作成
description: このレッスンでは、前のレッスンで学習した複数の概念を組み合わせて固有のサンプル エクスペリエンスを作成します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031550"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7.月着陸船サンプル アプリケーションの作成
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

このチュートリアルでは、前のレッスンの複数の概念を組み合わせて固有のサンプル エクスペリエンスを作成します。 ユーザーが追跡対象の手を使用して部品を選択し、月着陸船の組み立てを試みる必要がある部品アセンブリ アプリケーションを作成する方法について説明します。 押しボタンを使用して、配置のヒントのオン/オフを切り替えたり、エクスペリエンスをリセットしたり、月着陸船を宇宙に発射したりします。

今後のチュートリアルでは、空間的な位置合わせのために Azure Spatial Anchors を利用する強力なマルチユーザー ユースケースを含め、このエクスペリエンスを基に構築していきます。

## <a name="objectives"></a>目標

* 前のレッスンの複数の概念を組み合わせて固有のエクスペリエンスを作成する
* オブジェクトを切り替える方法を学習する
* 押しボタンを使用して複雑なイベントをトリガーする
* 剛体の物理学と力を使用する
* ヒントの使用を調査する

## <a name="lunar-module-parts-overview"></a>月着陸船部品の概要
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

このセクションでは、テーブル上に配置されている 5 つの部品を月着陸船の正しい位置に配置することをユーザーの目標とする、簡単な部品アセンブリの課題を作成します。

これを実現するための主な手順は次のとおりです。

1. ロケット発射台プレハブをシーンに追加する
2. すべての部品のオブジェクト操作を有効にする
3. Part Assembly Demo (Script) コンポーネントを追加して構成する

> [!NOTE]
> Part Assembly Demo (Script) コンポーネントは、MRTK の一部ではありません。 このチュートリアルのアセットと共に提供されました。

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1.ロケット発射台プレハブをシーンに追加する

[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)**  >  **[RocketLauncher]** フォルダーに移動し、 **[RocketLauncher]** プレハブを [Hierarchy]\(階層\) ウィンドウにドラッグしてシーンに追加し、適切な場所に配置します。次に例を示します。

* [Transform]\(変換\) の [Position]\(位置\) X = 1.5、Y = -0.4、Z = 0。これにより、ユーザーの右側に腰の高さで配置されます
* [Transform]\(変換\) の [Rotation]\(回転\) X = 0、Y = 180、Z = 0。これにより、エクスペリエンスの主な機能がユーザーに向けられます

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2.すべての部品のオブジェクト操作を有効にする

[Hierarchy]\(階層\) ウィンドウで、[RocketLauncher] > **[LunarModuleParts]** オブジェクトを見つけて、すべての**子オブジェクト**を選択します。次に、**Manipulation Handler (Script)** コンポーネントおよび **Near Interaction Grabbable (Script)** コンポーネントを追加し、Manipulation Handler (Script) を次のように構成します。

* **[Allow Far Manipulation]\(遠距離操作を許可\)** チェックボックスをオフにして、近距離操作のみを許可するようにします
* **[Two Handed Manipulation Type]\(両手を使った操作の種類\)** を **[Move Rotate]\(移動回転\)** に変更して、拡大縮小を無効にします

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> オブジェクトの操作を実装する方法の詳細な手順については、「[3D オブジェクトの操作](mrlearning-base-ch4.md#manipulating-3d-objects)」の説明を参照してください。

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3.Part Assembly Demo (Script) コンポーネントを追加して構成する

[LunarModuleParts] 子オブジェクトをすべて選択したまま、**Audio Source** コンポーネントを追加し、次のように構成します。

* 適切なオーディオ クリップ (たとえば MRKT_Scale_Start) を **[AudioClip]** フィールドに割り当てます
* **[Play On Awake]\(起動時に再生\)** チェックボックスをオフにして、シーンの読み込み時にオーディオ クリップが自動的に再生されないようにします
* **[Spatial Blend]\(空間ブレンド\)** を 1 に変更して、空間オーディオを有効にします

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

[LunarModuleParts] 子オブジェクトがすべて選択された状態で、**Part Assembly Demo  (Script)** コンポーネントを追加します。

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

[Hierarchy]\(階層\) ウィンドウで **[RoverEnclosure]** オブジェクトを選択し、**Part Assembly Demo (Script)** コンポーネントを次のように構成します。

* **[Object To Place]\(配置するオブジェクト\)** フィールドに、オブジェクト**自体** (この場合は RoverEnclosure オブジェクト) を割り当てます
* **[Location To Place]\(配置する場所\)** フィールドに、対応する **[PlacementHints]** オブジェクト (この場合は RoverEnclosure_PlacementHint オブジェクト) を割り当てます
* **[Tool Tip Object]\(ヒント オブジェクト\)** フィールドに、対応する **[ToolTip]** (この場合は RoverEnclosure_ToolTip オブジェクト) を割り当てます
* **[Audio Source]\(オーディオ ソース\)** フィールドに、オブジェクト**自体** (この場合は RoverEnclosure オブジェクト) を割り当てます

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

他のすべての LunarModuleParts 子オブジェクト (つまり、FuelTank、EnergyCell、DockingPortal、ExternalSensor) についても同じ手順を**繰り返します**。

ここでゲーム モードに入り、[Object To Place]\(配置するオブジェクト\) をそれに対応する [Location To Place]\(配置する場所\) の近くに配置すると、次のことが起こります。

* オブジェクトが所定の位置にはめ込まれ、LunarModule オブジェクトの下にペアレント化されて月着陸船の一部になります
* オブジェクトのオーディオ ソースは、オブジェクトの位置で割り当てられたオーディオ クリップを再生します
* 対応する Tool Tip オブジェクトは非表示になります

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> エディター内入力シミュレーションを使用する方法については、[MRTK ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) の[エディター内の手の入力シミュレーションを使用したシーンのテスト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)に関するガイドを参照してください。

## <a name="configuring-the-lunar-module"></a>月着陸船の構成

このセクションでは、ロケット発射台アプリケーションに機能を追加して、ユーザーが次のことができるようにします。

* 月着陸船を操作する
* 月着陸船を宇宙に打ち上げ、打ち上げ時にサウンドを再生する
* アプリケーションをリセットして、月着陸船とすべての部品を元の位置に戻す
* 配置ヒントを非表示にして、部品アセンブリの課題をより難しくする。

これを実現するための主な手順は次のとおりです。

1. オブジェクトの操作を有効にする
2. 物理的処理を有効にする
3. Audio Source コンポーネントを追加する
4. Launch Lunar Module (Script) コンポーネントを追加して構成する
5. Toggle Placement Hints (Script) コンポーネントを追加して構成する

> [!NOTE]
> Launch Lunar Module (Script) コンポーネントと Toggle Placement Hints (Script) コンポーネントは MRTK の一部ではありません。 これらはこのチュートリアルのアセットと共に提供されました。

### <a name="1-enable-object-manipulation"></a>1.オブジェクトの操作を有効にする

[Hierarchy]\(階層\) ウィンドウで、[RocketLauncher] > **[LunarModule]** オブジェクトを選択します。次に、**Manipulation Handler (Script)** コンポーネントおよび **Near Interaction Grabbable (Script)** コンポーネントを追加し、Manipulation Handler (Script) を次のように構成します。

* **[Allow Far Manipulation]\(遠距離操作を許可\)** チェックボックスをオフにして、近距離操作のみを許可するようにします
* **[Two Handed Manipulation Type]\(両手を使った操作の種類\)** を [Move Rotate]\(移動回転\) に変更して、拡大縮小を無効にします

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2.物理的処理を有効にする

[RocketLauncher] > **[LunarModule]** オブジェクトを選択したまま、**Rigidbody** コンポーネントを追加し、次のように構成します。

* **[Use Gravity]\(重力を使用\)** チェックボックスをオフにして、月着陸船が重力の影響を受けないようにします
* **[Is Kinematic]\(キネマティック\)** チェックボックスをオンにして、月着陸船が最初は物理的な力の影響を受けないようにします

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3.Audio Source コンポーネントを追加する

[RocketLauncher] > **[LunarModule]** オブジェクトを選択したまま、**Audio Source** コンポーネントを追加し、次のように構成します。

* **[Spatial Blend]\(空間ブレンド\)** を 1 に変更して、空間オーディオを有効にします

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4.Launch Lunar Module (Script) コンポーネントを追加して構成する

[RocketLauncher] > **[LunarModule]** オブジェクトを選択したまま、**Launch Lunar Module (Script)** コンポーネントを追加し、次のように構成します。

* **[Thrust]\(推力\)** の値を変更して、月着陸船が打ち上げ時に滑らかに上昇するようにします (たとえば、0.01)。

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5.Toggle Placement Hints (Script) コンポーネントを追加して構成する

[RocketLauncher] > **[LunarModule]** オブジェクトを選択したまま、**Toggle Placement Hints (Script)** コンポーネントを追加し、次のように構成します。

* ゲーム オブジェクト配列の **[Size]\(サイズ\)** プロパティを 5 に設定します
* 次のように、[RocketLauncher] > [LunarModule] > **[PlacementHints]** オブジェクトの**子オブジェクト**をゲーム オブジェクト配列の **[Element]\(要素\)** フィールドに割り当てます。

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>発射ボタンの構成

[Hierarchy]\(階層\) ウィンドウで、[RocketLauncher] > [Buttons] > **[LaunchButton]** オブジェクトを選択し、**Pressable Button (Script)** コンポーネントで、新しい **Button Pressed ()** イベントを作成し、イベントを受信するように **[LunarModule]** オブジェクトを構成して、トリガーするアクションとして **LaunchLunarModule.StartThruster** を定義します。

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> イベントを実装する方法については、「[手の追跡のジェスチャと操作可能なボタン](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)」の説明を参照してください。

[RocketLauncher] > [Buttons] > **[LaunchButton]** オブジェクトを選択したまま、**Pressable Button (Script)** コンポーネントで、新しい **Button Pressed ()** イベントを作成し、イベントを受信するように **[LunarModule]** オブジェクトを構成し、トリガーするアクションとして **AudioSource.PlayOneShot** を定義し、適切なオーディオ クリップ (MRTK_Gem オーディオ クリップなど) を **[Audio Clip]\(オーディオ クリップ\)** フィールドに割り当てます。

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

[RocketLauncher] > [Buttons] > **[LaunchButton]** オブジェクトを選択したまま、**Pressable Button (Script)** コンポーネントで、新しい **Touch End ()** イベントを作成し、イベントを受信するように **[LunarModule]** オブジェクトを構成して、トリガーするアクションとして **LaunchLunarModule.StopThruster** を定義します。

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

ここでゲーム モードに入り、[Launch]\(発射\) ボタンを押すと、オーディオ クリップが再生されます。また、[Launch]\(発射\) ボタンを 1 秒以上押し続けると、月着陸船が宇宙に打ち上げられます。

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>リセット ボタンの構成

[Hierarchy]\(階層\) ウィンドウで、[RocketLauncher] > [Buttons] > **[ResetButton]** オブジェクトを選択し、**Pressable Button (Script)** コンポーネントで、新しい **Button Pressed ()** イベントを作成し、イベントを受信するように **[LunarModule]** オブジェクトを構成して、トリガーするアクションとして **LaunchLunarModule.ResetModule** を定義します。

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

[RocketLauncher] > [Buttons] > **[ResetButton]** オブジェクトを選択したまま、**Pressable Button (Script)** コンポーネントで、新しい **Button Pressed ()** イベントを作成し、イベントを受信するように **[RocketLauncher]** オブジェクトを構成して、トリガーするアクションとして **GameObject.BroadcastMessage** を定義し、メッセージ フィールドに **ResetPlacement** と入力します。

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> GameObject.BroadcastMessage アクションは、RocketLauncher オブジェクトからそのすべての子オブジェクトに ResetPlacement メッセージを 送信します。 すべての LunarModuleParts 子オブジェクトに追加した Part Assembly Demo (Script) コンポーネントで定義されている ResetPlacement 関数を持つすべての子オブジェクトは、その子オブジェクトの配置をリセットする ResetPlacement 関数を呼び出します。

ここでゲーム モードに入り、部品を移動するか月着陸船を発射してから [Reset]\(リセット\) ボタンを押すと、部品または月着陸船は元の位置にリセットされます。

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>配置のヒント ボタンの構成
<!-- TODO: Rename to 'Configuring the Hints button'-->

[Hierarchy]\(階層\) ウィンドウで、[RocketLauncher] > [Buttons] > **[HintsButton]** オブジェクトを選択し、**Pressable Button (Script)** コンポーネントで、新しい **Button Pressed ()** イベントを作成し、イベントを受信するように **[LunarModule]** オブジェクトを構成して、トリガーするアクションとして **TogglePlacementHints.ToggleGameObjects** を定義します。

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

ここでゲーム モードに入ると、半透明の配置ヒントは既定で無効になっていますが、[Hints]\(ヒント\) ボタンを押すことによって、オンとオフを切り替えることができます。

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>結論

このアプリケーションが完全に構成されました。 これでユーザーは、このアプリケーションを使用して月着陸船を完全に組み立て、月着陸船を発射し、ヒントを切り替え、アプリケーションをリセットして再び開始することができるようになりました。
