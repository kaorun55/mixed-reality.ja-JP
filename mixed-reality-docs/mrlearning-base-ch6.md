---
title: 入門チュートリアル-7. 旧暦モジュールサンプルアプリケーションの作成
description: このレッスンでは、前のレッスンから学習した複数の概念を組み合わせて固有のサンプル エクスペリエンスを作成します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 97dd8fce1ebe53efc37cb48cde7dc9e207be9a42
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701993"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7.旧暦モジュールサンプルアプリケーションの作成

このチュートリアルでは、前のレッスンで説明した複数の概念を組み合わせて、独自のサンプルエクスペリエンスを作成します。 旧暦モジュールアセンブリアプリケーションを作成します。このアプリケーションでは、ユーザーが追跡したハンドを使用して旧暦モジュールパーツを取得し、旧暦モジュールを組み立てるようにします。 Pressable ボタンを使用して配置ヒントを切り替え、エクスペリエンスをリセットして、旧暦モジュールをスペースで起動します。 今後のチュートリアルでは、このエクスペリエンスの構築を続けています。これには、空間アラインメントに Azure 空間アンカーを利用する強力なマルチユーザーユースケースが含まれます。

## <a name="objectives"></a>目的

- 前のレッスンの複数の概念を組み合わせて固有のエクスペリエンスを作成する
- オブジェクトを切り替える方法を学習する
- 押しボタンを使用して複雑なイベントをトリガーする
- 剛体の物理学と力を使用する
- ヒントの使用を調査する

## <a name="instructions"></a>手順

### <a name="configuring-the-lunar-module"></a>月着陸船の構成

このセクションでは、サンプルエクスペリエンスを作成するために必要なさまざまなコンポーネントについて説明します。

1. 基本シーンに旧暦モジュールアセンブリ prefab を追加します。 これを行うには、[プロジェクト] タブで、ロケット Launcher_Tutorial を検索します。 
「Assets-> BaseModuleAssets-> Prefabs」で prefab を見つけます。 また、2つのロケットランチャー prefabs も表示されます。1つは "チュートリアル" という名前で、もう1つは "complete" という名前です。 ロケット Launcher_Tutorial prefab を基本シーンにドラッグし、必要に応じて位置を移動します。
   注:ロケット Launcher_Complete prefab は、参照用に用意された、完成したランチャーです。 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

階層内でロケット Launcher_Tutorial game オブジェクトを展開し、さらに太陰暦モジュールオブジェクトをさらに展開すると、"x 射線" という名前の素材を持ついくつかの子オブジェクトが見つかります。 "X 射線" のマテリアルでは、ユーザーの配置ヒントとして使用する半透明色を使用できます。 

![Lesson6 chapter1.txt](images/Lesson6_Chapter1_noteaim.PNG)については、次の図に示すように、ユーザーが対話する、太陰暦モジュールに5つの部分があります。

1.  探査車格納庫
2.  燃料タンク
3.  エネルギー セル
4.  ドッキング ポータル 
5.  外部センサー

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> 注:基本のシーン階層に表示されるゲームオブジェクト名は、シーン内のオブジェクトの名前に対応していません。

手順 2:月着陸船にオーディオ ソースを追加します。 基本のシーン階層で旧暦モジュールが選択されていることを確認し、[コンポーネントの追加] をクリックします。 オーディオソースを検索し、それをオブジェクトに追加します。 今は空白のままにします。 これは、後で発射音を再生するために使用します。

 ![Lesson6 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)  
手順 3:スクリプトを追加し、配置ヒントを切り替えます。 [コンポーネントの追加] をクリックし、[配置ヒントの切り替え] を検索します。 これは、前に説明した半透明なヒント (x 線を持つオブジェクト) のオンとオフを切り替えることができるカスタムスクリプトです。  
![Lesson6 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)  
手順 4:5つのオブジェクトがあるため、game オブジェクトの配列サイズとして「5」と入力します。 5つの新しい要素が表示されます。  


![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

各半透明オブジェクトを [すべての名前 (Game Obect)] ボックスにドラッグします。
[Base Scene] の月着陸船の次のオブジェクトをドラッグします。 

•   Backpack

•   GasTank

•   Topleftbody

•   Nose

•   LeftTwirler

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

これで、配置ヒントの切り替えスクリプトが構成されました。 これにより、ヒントを有効または無効にすることができます。

手順 5:Launch 旧暦モジュールスクリプトを追加します。 [コンポーネントの追加] ボタンをクリックし、"launch 旧暦モジュール" を検索して選択します。 このスクリプトは、旧暦モジュールを起動します。 構成されたボタンを押したときに、旧暦モジュールの固定本文コンポーネントに上位の力を追加し、モジュールを上方に起動します。 屋内にいる場合は、月着陸船が天井メッシュに当たってクラッシュする可能性があります。 ただし、屋外にいる場合は、宇宙をいつまでも飛行します。 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

手順 6:月着陸船が正常に上に向かって飛行するように [推進力] を調整します。 0\.01 の値を試してください。 [Rb] フィールドは空白のままにします。 Rb は剛体を表し、このフィールドは実行時に自動的にデータが入力されます。

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>旧暦モジュールパーツの概要
旧暦モジュールパーツの親オブジェクトは、ユーザーが操作するオブジェクトのコレクションです。 Paretheses に名前が付いているシーンを含む Game オブジェクト名は、次の一覧に示されています。

- Backpack (燃料タンク)
- GasTank (エネルギー セル)
- TopLeftBody (探査車格納庫)
- Nose (ドッキング ポータル)
- LeftTwirler (外部センサー)

これらの各オブジェクトには、レッスン4で説明した操作ハンドラーがあることに注意してください。 操作ハンドラーを使用すると、ユーザーはオブジェクトを取得して操作できます。 また、設定 [2 つのきき操作の種類] が [移動と回転] に設定されていることにも注意してください。 これにより、ユーザーはオブジェクトを移動することしかできず、サイズは変更できません。これは、アセンブリ アプリケーションには望ましい機能です。
さらに、モジュールパーツを直接やり取りするためだけに、遠くの操作はオフになっています。

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

部分アセンブリデモスクリプト (上図参照) は、ユーザーがユーザーによってユーザーが旧暦モジュールに配置するオブジェクトを管理するスクリプトです。 

フィールドを配置するオブジェクトは、上の図に示すように選択されている変換です。これは、接続先のオブジェクトに関連付けられている backpack/燃料タンクです。 

近距離距離と遠く距離の設定によって、どのパーツがどこに配置されているか、または解放できるかが決まります。 たとえば、backpack/燃料タンクは、位置に合わせる前に、旧暦モジュールから離れた0.1 単位である必要があります。 [遠くの距離] 設定では、オブジェクトが旧暦モジュールからデタッチできるようになる位置が設定されます。 この場合、ユーザーの手は Backpack/燃料タンクをつかみ、再度はめ込まれないように取り外すには月着陸船から 0.2 ユニット離れた場所に引く必要があります。

ツールヒントオブジェクトはシーンのツールヒントラベルです。 オブジェクトが所定の位置にスナップされると、ラベルは無効になります。 

オーディオソースが自動的にグラブされます。 

### <a name="placement-hints-buttons"></a>配置ヒントボタン
[レッスン 2](mrlearning-base-ch2.md) では、項目の色を変更したり、押されたら音を再生したりするなどの操作を実行するためのボタンを配置および構成する方法を学習しました。 ここでは配置のヒントを切り替えるためのボタンを構成するため、これらの原則を引き続き使用します。 

目標は、ユーザーが配置ヒントボタンを押すたびに、半透明の配置ヒントが表示されるように、ボタンを構成することです。 

手順 1:基本のシーン階層で配置ヒントオブジェクトが選択されている間、[インスペクター] パネルの空のランタイムのみのスロットに旧暦モジュールを移動します。 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 手順 2:次に、[関数なし] ドロップダウンリストをクリックします。 TogglePlacementHints に移動し、そのメニューの [ToggleGameObjects ()] を選択します。 ToggleGameObjects () は、ボタンが押されるたびに表示または非表示になるように配置ヒントのオンとオフを切り替えます。  
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>[リセット] ボタンの構成

ユーザーが間違っている場合や、誤ってオブジェクトを破棄した場合や、エクスペリエンスをリセットしたい場合があります。 [リセット] ボタンをクリックすると、エクスペリエンスを再起動する機能が追加されます。 

手順 1:[リセット] ボタンを選択します。 基本シーンでは、ResetRoundButton という名前が付けられます。 

手順 2:[インスペクター] パネルの [Button] の下にある空のスロットに、[基本シーン] 階層から旧暦モジュールをドラッグします。
 ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

手順 3:[関数なし] ドロップダウンメニューを選択し、LaunchLunarModule の上にポインターを合わせ、resetModule () を選択します。

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> 注:既定では、BroadcastMessage は ResetPlacement に構成されていることに注意してください。 これにより、RocketLauncher_Tutorial のすべての子オブジェクトに対する ResetPlacement というメッセージがブロードキャストされます。 ResetPlacement () のメソッドを持つオブジェクトは、位置をリセットすることによって、そのメッセージに応答します。 

### <a name="launching-the-lunar-module"></a>旧暦モジュールを起動しています
このセクションでは、起動ボタンの構成方法を explaings します。 これにより、ユーザーはボタンを押して、旧暦モジュールをスペースで起動できます。

手順 1:[起動] ボタンを選択します。 それが呼び出される基本シーンでは、LaunchRoundButton になります。 [インスペクター] パネルの [タッチエンド] の下にある空のスロットに、旧暦モジュールをドラッグします。
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 手順 2:[関数なし] ドロップダウンメニューを選択し、LaunchLunarModule の上にマウスポインターを移動し、[StopThruster ()] を選択します。 これにより、ユーザーが旧暦モジュールに与える推力の量が制御されます。 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)  
手順 3:ButtonPressed れた () の下で、空のスロットに旧暦モジュール (クリック、ホールド、ドラッグ) を追加します。 

手順 4:[関数なし] ドロップダウンメニューをクリックし、LaunchLunarModule の上にマウスポインターを移動し、[StartThruster ()] を選択します。 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)  
手順 5:音楽がロケットの撮影時に再生されるように、旧暦モジュールに音楽を追加します。 これを行うには、[] ボタンが押された状態の次の空のスロット () に旧暦モジュールをドラッグします。

手順 6:[関数なし] ドロップダウンメニューを選択し、AudioSource の上にマウスポインターを移動して、[PlayOneShot (Audiosource)] を選択します。 MRTK に含まれているさまざまな音から自由に選択してください。 この例では、"MRTK_Gem" を使用します。
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>結論 
このアプリケーションは完全に構成されています。 ここで、[再生] をクリックすると、旧暦モジュールを完全に組み立て、ヒントを切り替えることができます。さらに、旧暦モジュールを起動してリセットし、再起動してもう一度開始します。
