---
title: MR 学習ベース モジュール - 月着陸船アセンブリのサンプル エクスペリエンス
description: このレッスンでは、前のレッスンから学習した複数の概念を組み合わせて固有のサンプル エクスペリエンスを作成します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730845"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>MR 学習ベース モジュール - 月着陸船アセンブリのサンプル エクスペリエンス

このレッスンでは、前のレッスンから学習した複数の概念を組み合わせて固有のサンプル エクスペリエンスを作成します。 ユーザーが追跡対象の手を使用して月着陸船の部品を持ち上げ、月着陸船の組み立てを試みる必要がある月着陸船アセンブリ アプリケーションを作成します。 押しボタンを使用して、配置のヒントを切り替えたり、エクスペリエンスをリセットしたり、月着陸船を宇宙に発射したりします。 将来のチュートリアルでは、空間的整合のために Azure Spatial Anchors を利用する強力なマルチユーザー ユースケースを含め、引き続きこのエクスペリエンスの上に構築します。

## <a name="objectives"></a>目標

- 前のレッスンの複数の概念を組み合わせて固有のエクスペリエンスを作成する
- オブジェクトを切り替える方法を学習する
- 押しボタンを使用して複雑なイベントをトリガーする
- 剛体の物理学と力を使用する
- ヒントの使用を調査する

## <a name="instructions"></a>手順

### <a name="configuring-the-lunar-module"></a>月着陸船の構成

この章では、サンプル エクスペリエンスを作成するために必要なさまざまなコンポーネントを導入します。

1. 月着陸船アセンブリ プレハブを [Base Scene] に追加します。 これを行うには、プロジェクト タブで [Rocket Launcher_Tutorial] を検索します。 このプレハブは、[アセット]>[BaseModuleAssets]>[プレハブ] で見つけることもできます。 2 つのロケット発射台プレハブが表示されます。1 つは [チュートリアル] という名前であり、もう 1 つは [完成] という名前です。 [Rocket Launcher_Tutorial] プレハブを [Base Scene] にドラッグします。 プレハブの位置をシーン内に自由に配置してください。
   注:[Rocket Launcher_Complete] プレハブは、参考のために提供されている完成した発射台です。 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

階層内で [Rocket Launcher_Tutorial] ゲーム オブジェクトを展開し、さらに [月着陸船] オブジェクトを展開すると、[X 線] という名前の素材を持ついくつかの子オブジェクトが表示されます。 [X 線] 素材では、ユーザーへの配置のヒントとして使用する、わずかに半透明な色が可能になります。 

![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) 次の図に示すように、月着陸船には、ユーザーが操作する 5 つの部品があります。

1.  探査車格納庫
2.  燃料タンク
3.  エネルギー セル
4.  ドッキング ポータル 
5.  外部センサー

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> 注:[Base Scene] 階層に表示されるゲーム オブジェクト名は、シーン内のオブジェクトの名前に対応していません。

手順 2:月着陸船にオーディオ ソースを追加します。 [Base Scene] 階層で月着陸船が選択されていることを確認し、[コンポーネントの追加] をクリックします。 [オーディオ ソース] を検索し、それをオブジェクトに追加します。 今は空白のままにします。 これは、後で発射音を再生するために使用します。
 ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) 手順 3:[配置のヒントを切り替える] スクリプトを追加します。 [コンポーネントの追加] をクリックし、[配置のヒントを切り替える] を検索します。 これは、先に説明した半透明なヒント (X 線素材を持つオブジェクト) のオンとオフを切り替えることができるカスタム スクリプトです。 
![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) 手順 4:5 つのオブジェクトがあるため、ゲーム オブジェクト配列のサイズに「5」と入力します。 それにより、5 つの新しい要素が表示されます。 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

半透明な各オブジェクトを [なし (ゲーム オブジェクト)] が表示されたボックスにドラッグします。 [Base Scene] の月着陸船の次のオブジェクトをドラッグします。 

•   Backpack

•   GasTank

•   Topleftbody

•   Nose

•   LeftTwirler

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

これで、[配置のヒントを切り替える] スクリプトが構成されました。 これにより、ヒントのオンとオフを切り替えることができます。

手順 5:[月着陸船を発射する] スクリプトを追加します。 [コンポーネントの追加] ボタンをクリックし、[月着陸船を発射する] を検索して選択します。 このスクリプトには、月着陸船を発射する役割があります。 構成されたボタンを押すと、月着陸船の剛体コンポーネントに上向きの力が加えられ、この月着陸船が上に向けて発射されます。 屋内にいる場合は、月着陸船が天井メッシュに当たってクラッシュする可能性があります。 ただし、屋外にいる場合は、宇宙をいつまでも飛行します。 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

手順 6:月着陸船が正常に上に向かって飛行するように [推進力] を調整します。 0\.01 の値を試してください。 [Rb] フィールドは空白のままにします。 Rb は剛体を表し、このフィールドは実行時に自動的にデータが入力されます。

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>[月着陸船] 部品の概要
[月着陸船] 部品の親オブジェクトは、ユーザーが操作するオブジェクトのコレクションです。 ゲーム オブジェクト名 (かっこ内はシーンのラベルが付いた名前) を次の一覧に示します。

- Backpack (燃料タンク)
- GasTank (エネルギー セル)
- TopLeftBody (探査車格納庫)
- Nose (ドッキング ポータル)
- LeftTwirler (外部センサー)

レッスン 4 で説明されているように、これらの各オブジェクトには操作ハンドラーかあることに注意してください。 操作ハンドラーを使用すると、ユーザーはオブジェクトをつかんで操作できます。 また、[両手を使った操作の種類] 設定が [移動と回転] に設定されていることにも注意してください。 これにより、ユーザーはオブジェクトを移動することしかできず、サイズは変更できません。これは、アセンブリ アプリケーションには望ましい機能です。
さらに、月着陸船の部品の直接操作のみを許可するために、遠隔操作はオフになっています。

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

部品アセンブリ デモ スクリプト (上に示されています) は、ユーザーによって月着陸船に配置されるオブジェクトを管理するスクリプトです。 

[配置するオブジェクト] フィールドは、接続できるオブジェクトと共に選択された変換 (前の図の場合は、Backpack/燃料タンク) です。 

[近距離] および [遠距離] 設定には、部品をはめ込んだり、取り外したりするときの近さを決定する役割があります。 たとえば、Backpack/燃料タンクは、はめ込むには月着陸船から 0.1 ユニット離れている必要があります。 [遠距離] は、オブジェクトを月着陸船から取り外す必要がある場所を設定します。 この場合、ユーザーの手は Backpack/燃料タンクをつかみ、再度はめ込まれないように取り外すには月着陸船から 0.2 ユニット離れた場所に引く必要があります。

[ヒント オブジェクト] は、シーン内のヒント ラベルです。 オブジェクトがはめ込まれると、ラベルは無効になります。 

オーディオ ソースは自動的に取り込まれます。 

### <a name="placement-hints-buttons"></a>[配置のヒント] ボタン
[レッスン 2](mrlearning-base-ch2.md) では、項目の色を変更したり、押されたら音を再生したりするなどの操作を実行するためのボタンを配置および構成する方法を学習しました。 ここでは配置のヒントを切り替えるためのボタンを構成するため、これらの原則を引き続き使用します。 

目標は、ユーザーが [配置のヒント] ボタンを押すたびに、半透明な配置のヒントの可視性を切り替えるようにボタンを構成することです。 

手順 1:[Base Scene] 階層で [配置のヒント] オブジェクトが選択されているときに、[月着陸船] を [インスペクター] パネルの空の [ランタイムのみ] スロットに移動します。 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 手順 2:ここで、[関数なし] が表示されたドロップダウン リストをクリックします。 下の方の [TogglePlacementHints] に移動し、そのメニューの下の [ToggleGameObjects ()] を選択します。 ToggleGameObjects() は、配置のヒントのオンとオフを切り替えて、ボタンが押されるたびに表示または非表示になるようにします。
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>リセット ボタンの構成

ユーザーが間違いを犯したり、オブジェクトを誤って捨てたり、単にエクスペリエンスを停止させたくなったりする状況が発生します。 リセット ボタンにより、エクスペリエンスを再開する機能が追加されます。 

手順 1:リセット ボタンを選択します。 [Base Scene] では [ResetRoundButton] という名前になっています。 

手順 2:[Base Scene] 階層の [月着陸船] を、[インスペクター] パネルの [Button Pressed] の下の空のスロットにドラッグします。
 ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

手順 3:[関数なし] が表示されたドロップダウン メニューを選択し、[LaunchLunarModule] にマウス ポインターを置きます ここで [resetModule ()] を選択します。

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> 注:既定では、[GameObject.BroadcastMessage] が [ResetPlacement] に構成されていることに注意してください。 これにより、RocketLauncher_Tutorial のすべての子オブジェクトに [ResetPlacement] という名前のメッセージがブロードキャストされます。 [ResetPlacement()] 用のメソッドを持つオブジェクトはすべて、その位置をリセットすることによってそのメッセージに応答します。 

### <a name="launching-the-lunar-module"></a>月着陸船の発射
この章では、発射ボタンを構成します。 これにより、ユーザーはそのボタンを押して月着陸船を宇宙に発射することができます。

手順 1:発射ボタン ([Base Scene] では [LaunchRoundButton] という名前になっています) を選択します。 [月着陸船] を [インスペクター] パネルの [タッチ終了] の下の空のスロットにドラッグします。
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 手順 2:[関数なし] が表示されたドロップダウン メニューを選択します。 [LaunchLunarModule] にマウス ポインターを置いて [StopThruster ()] を選択します。 これにより、ユーザーが月着陸船にどれだけの推進力を与えるかが制御されます。 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) 手順 3:[ButtonPressed()] の下で、[月着陸船] を空のスロットに追加 (クリック、保持、ドラッグ) します。 

手順 4:[関数なし] が表示されたドロップダウン メニューをクリックし、[LaunchLunarModule] にマウス ポインターを置いて [StartThruster ()] を選択します。 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) 手順 5:ロケットが発射したら音楽が再生されるように、月着陸船に音楽を追加します。 これを行うには、[月着陸船] を [Button Pressed()] の下の次の空のスロットにドラッグします。

手順 6:[関数なし] が表示されたドロップダウン メニューを選択し、[AudioSource] にマウス ポインターを置いて [PlayOneShot (AudioClip)] を選択します。 MRTK に含まれているさまざまな音から自由に選択してください。 この例では、[MRTK_Gem] を使用します。
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>結論 
このアプリケーションが完全に構成されました。 これで [再生] を押せば、月着陸船を完全に組み立てたり、ヒントを切り替えたり、月着陸船を発射したり、始めからやり直すためにリセットしたりすることができます。
