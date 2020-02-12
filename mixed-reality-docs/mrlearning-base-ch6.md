---
title: 入門チュートリアル-7. 旧暦モジュールサンプルアプリケーションの作成
description: このレッスンでは、前のレッスンで学習した複数の概念を組み合わせて、独自のサンプルエクスペリエンスを作成します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: b5b1bd0115822449bd6098f78cfc94d909169737
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129452"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. 旧暦モジュールサンプルアプリケーションを作成する
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

このチュートリアルでは、前のレッスンとの複数の概念を組み合わせて、独自のサンプルエクスペリエンスを作成します。 パートアセンブリアプリケーションを作成する方法を学習します。このアプリケーションでは、ユーザーが追跡したハンドを使用して部品を取り出し、旧暦モジュールを組み立てる必要があります。 Pressable ボタンを使用して、配置ヒントのオンとオフを切り替えたり、エクスペリエンスをリセットしたり、旧暦モジュールをスペースで起動したりします。

今後のチュートリアルでは、このエクスペリエンスの構築を継続します。これには、空間の配置に Azure 空間アンカーを利用する強力なマルチユーザーのユースケースが含まれます。

## <a name="objectives"></a>目標

* 前のレッスンの複数の概念を組み合わせて固有のエクスペリエンスを作成する
* オブジェクトを切り替える方法を学習する
* 押しボタンを使用して複雑なイベントをトリガーする
* 剛体の物理学と力を使用する
* ヒントの使用を調査する

## <a name="lunar-module-parts-overview"></a>旧暦モジュールパーツの概要
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

このセクションでは、簡単なパートアセンブリチャレンジを作成します。ユーザーの目標は、テーブルに展開される5つの部分を太陰暦モジュールの正しい位置に配置することです。

これを実現するには、主に次の手順を実行します。

1. ロケットランチャー prefab をシーンに追加する
2. すべての部分に対してオブジェクトの操作を有効にする
3. パーツアセンブリのデモ (スクリプト) コンポーネントを追加して構成する

> [!NOTE]
> パートアセンブリデモ (スクリプト) コンポーネントは、MRTK の一部ではありません。 このチュートリアルでは、このチュートリアルのアセットを提供しました。

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. ロケットランチャー prefab をシーンに追加する

プロジェクト ウィンドウで、**アセット** >  **mrtk に移動します。チュートリアル: GettingStarted** **Prefabs** > **RocketLauncher**フォルダーに移動し、 **RocketLauncher** prefab を 階層 ウィンドウにドラッグしてシーンに追加した後、適切な場所に配置します。次に例を示します。 > 

* 変換位置 X = 1.5、Y =-0.4、Z = 0 の場合、ユーザーの右側にウェスト height で配置されます。
* 変換の回転 X = 0、Y = 180、Z = 0、エクスペリエンスの主な機能はユーザーにとって

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. すべての部分に対してオブジェクトの操作を有効にします。

[階層] ウィンドウで、RocketLauncher > **Lunarmoduleparts**オブジェクトを見つけてすべての**子オブジェクト**を選択し、**操作ハンドラー (スクリプト)** コンポーネントと**Near Grabbable (スクリプト**) コンポーネントを追加して、操作ハンドラー (スクリプト) を次のように構成します。

* **2 つのきき操作の種類**を移動回転に変更して、スケーリングが無効になるようにします。
* [**遠隔操作を許可**する] チェックボックスをオフにして、ほぼ対話のみを許可します。

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> オブジェクトの操作を実装する方法に関する詳細な手順については、「 [3D オブジェクトの操作](mrlearning-base-ch4.md#manipulating-3d-objects)」の指示を参照してください。

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. パーツアセンブリのデモ (スクリプト) コンポーネントを追加して構成する

すべての LunarModuleParts 子オブジェクトを選択したまま、**オーディオソース**コンポーネントを追加し、次のように構成します。

* 適切なオーディオクリップを**audioclip**フィールドに割り当てます (たとえば、MRKT_Scale_Start
* シーンの読み込み時にオーディオクリップが自動的に再生されないように、 **[スリープ状態で再生]** チェックボックスをオフにします。
* 空間**Blend**を1に変更して、空間オーディオを有効にする

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

すべての LunarModuleParts 子オブジェクトがまだ選択されている状態で、 **Part Assembly Demo (スクリプト)** コンポーネントを追加します。

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

[階層] ウィンドウで、 **Roverenclosure クロージャ**オブジェクトを選択し、その**パートアセンブリデモ (スクリプト)** コンポーネントを次のように構成します。

* フィールドを**配置するオブジェクト**に対して、オブジェクト自体 (この場合は**roverenclosure クロージャ**オブジェクト) を割り当てます。
* **[場所]** フィールドに、対応する PlacementHints オブジェクト (この例では**RoverEnclosure_PlacementHints**オブジェクト) を割り当てます。
* **ツールヒントオブジェクト**フィールドに、対応する ToolTipObject (この例では**RoverEnclosure_ToolTip**オブジェクト) を割り当てます。
* **[オーディオソース]** フィールドに、オブジェクト自体 (この場合は**roverenclosure クロージャ**オブジェクト) を割り当てます。

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

他のすべての LunarModuleParts 子オブジェクト (つまり、Futex、EnergyCell、DockingPortal、ExternalSensor) に対して**繰り返し**ます。

ここでゲームモードに入り、' オブジェクト ' を移動して、それに対応する ' Location ' の位置に近い場所に配置すると、次のことがわかります。

* オブジェクトが配置され、LunarModule オブジェクトの親になります。これにより、オブジェクトが旧暦モジュールの一部になります。
* オブジェクトのオーディオソースは、オブジェクトの位置で割り当てられたオーディオクリップを再生します。
* 対応するツールヒントオブジェクトは非表示になります

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> エディター内入力シミュレーションの使用方法に関する注意事項については、「エディターでの入力シミュレーションを使用して、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)でシーンガイドを[テストする](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)」を参照してください。

## <a name="configuring-the-lunar-module"></a>月着陸船の構成

このセクションでは、ユーザーが次のことができるように、ロケットランチャーアプリケーションに機能を追加します。

* 旧暦モジュールとの対話
* 旧暦モジュールをスペースで起動し、起動時にサウンドを再生します。
* 旧暦モジュールとすべての部分が元の位置に戻されるようにアプリケーションをリセットします。
* パーツアセンブリのチャレンジをより困難にするために配置ヒントを非表示にします。

これを実現するには、主に次の手順を実行します。

1. オブジェクトの操作を有効にする
2. 物理を有効にする
3. オーディオソースコンポーネントを追加する
4. Launch 旧暦モジュール (スクリプト) コンポーネントの追加と構成
5. 配置ヒントの切り替え (スクリプト) コンポーネントの追加と構成

> [!NOTE]
> [旧暦モジュール (スクリプト)] コンポーネントと [配置ヒントの切り替え (スクリプト)] コンポーネントは、MRTK の一部ではありません。 これらは、このチュートリアルの資産で提供されています。

### <a name="1-enable-object-manipulation"></a>1. オブジェクトの操作を有効にする

[階層] ウィンドウで、RocketLauncher > **Lunarmodule**オブジェクトを選択し、**操作ハンドラー (スクリプト)** コンポーネントと**Near Grabbable (スクリプト)** コンポーネントを追加して、操作ハンドラー (スクリプト) を次のように構成します。

* **2 つのきき操作の種類**を移動回転に変更して、スケーリングが無効になるようにします。
* [**遠隔操作を許可**する] チェックボックスをオフにして、ほぼ対話のみを許可します。

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. 物理を有効にする

RocketLauncher > **Lunarmodule**オブジェクトを選択したまま、Rigidbody コンポーネントを追加し、次のように構成します。

* **[重力を使用する]** チェックボックスをオフにして、太陰暦モジュールが重力の影響を受けないようにします。
* **[Is キネマティック]** チェックボックスをオンにします。これにより、旧暦モジュールは、physic の強制による影響を受けません。

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. オーディオソースコンポーネントを追加する

RocketLauncher > **Lunarmodule**オブジェクトを選択したまま、**オーディオソース**コンポーネントを追加し、次のように構成します。

* 空間**Blend**を1に変更して空間オーディオを有効にする

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. Launch Module (スクリプト) コンポーネントを追加して構成する

RocketLauncher > **Lunarmodule**オブジェクトを選択した状態で、 **Launch 旧暦モジュール (スクリプト)** コンポーネントを追加し、次のように構成します。

* **推力**の値を変更して、旧暦を起動したときに (たとえば、0.01 に)、旧暦のモジュールが適切に表示されるようにします。

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. 配置ヒントの切り替え (スクリプト) コンポーネントを追加および構成する

RocketLauncher > **Lunarmodule**オブジェクトを選択したまま、 **[配置ヒント (スクリプト) の切り替え]** コンポーネントを追加し、次のように構成します。

* Game オブジェクトの配列**サイズ**プロパティを5に設定します。
* **PlacementHints**オブジェクトの各**子オブジェクト**を、Game オブジェクト配列の**要素**フィールドに割り当てます。

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>[起動] ボタンの構成

[階層] ウィンドウで、[> RocketLauncher] ボタン > **launchbutton**オブジェクトを選択し、[ **Pressable] ボタン (スクリプト)** コンポーネントで新しい**ボタン押された ()** イベントを作成して、イベントを受信するための**lunarmodule**オブジェクトを構成し、トリガーするアクションとして**launchlunarStartThruster**を定義します。

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> イベントの実装方法に関する注意事項については、「[ハンドトラッキングジェスチャ」と「対話型 buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 」を参照してください。

RocketLauncher > ボタン > **launchbutton**オブジェクトが選択された状態で、[ **Pressable] ボタン (スクリプト)** コンポーネントで、新しい**Button 押された ()** イベントを作成し、イベントを受信するように**lunarmodule**オブジェクトを構成し、トリガーするアクションとして**audiosource. PlayOneShot**を定義し **、オーディオクリップフィールドに**適切 MRTK_Gem なオーディオクリップを割り当てます

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

RocketLauncher > ボタン > **launchbutton**オブジェクトが選択された状態で、[ **Pressable] ボタン (スクリプト)** コンポーネントで新しい**タッチ終了 ()** イベントを作成し、イベントを受信するように**lunarmodule**オブジェクトを構成して、トリガーされるアクションとして**launchlunarmodule. StopThruster**を定義します。

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

これでゲームモードに入り、[起動] ボタンを押すと、オーディオクリップが再生されます。また、[起動] ボタンを1秒以上押したままにすると、旧暦モジュールがスペースで起動していることがわかります。

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>[リセット] ボタンの構成

[階層] ウィンドウで、[RocketLauncher >] ボタン > **Resetbutton**オブジェクトを選択し、[ **Pressable] ボタン (スクリプト)** コンポーネントで新しい**Button 押された ()** イベントを作成します。次に、イベントを受信するための**lunarmodule**オブジェクトを構成し、トリガーするアクションとして**launchlunarmodule. resetbutton**を定義します。

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

RocketLauncher > のボタン > **resetbutton**オブジェクトを選択したまま、[ **Pressable] ボタン (スクリプト)** コンポーネントで、新しい**Button 押された ()** イベントを作成し、イベントを受信するように**RocketLauncher**オブジェクトを構成し、トリガーするアクションとして**BroadcastMessage**を定義し、メッセージフィールドに**resetbutton**を入力します。

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> BroadcastMessage アクションは、ResetPlacement メッセージを RocketLauncher オブジェクトからすべての子オブジェクトに送信します。 すべての LunarModuleParts 子オブジェクトに追加したパーツアセンブリデモ (スクリプト) コンポーネントで定義されている ResetPlacement 関数を持つ子オブジェクトは、その子オブジェクトの配置をリセットする ResetPlacement 関数を呼び出します。

これでゲームモードに入り、[リセット] ボタンを押すと、再生中のオーディオクリップが表示され、スペースで開かれている旧暦が表示されます。

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>配置ヒントボタンの構成
<!-- TODO: Rename to 'Configuring the Hints button'-->

[階層] ウィンドウで、[RocketLauncher > ボタン > **Hintsbutton]** オブジェクトを選択し、[ **Pressable] ボタン (スクリプト)** コンポーネントで新しい**ボタン押された ()** イベントを作成します。次に、イベントを受信するための**lunarmodule**オブジェクトを構成し、トリガーされるアクションを**TogglePlacementHints**に定義します。

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

これでゲームモードに入ると、半透明の配置ヒントが既定で無効になっていることがわかりますが、ヒントボタンを押すことによって、オンとオフを切り替えることができます。

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>結論

このアプリケーションは完全に構成されています。 これで、アプリケーションでは、ユーザーが旧暦モジュールを完全に組み立て、旧暦モジュールを起動し、ヒントを切り替えることができるようになりました。また、アプリケーションをリセットして再起動することもできます。
