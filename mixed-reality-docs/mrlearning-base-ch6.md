---
title: 入門チュートリアル-7. 旧暦モジュールサンプルアプリケーションの作成
description: このレッスンでは、前のレッスンで学習した複数の概念を組み合わせて、独自のサンプルエクスペリエンスを作成します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: a4f405b29ac87945a8585beeed83c1beb450eb0e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437756"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. 旧暦モジュールサンプルアプリケーションを作成する

このチュートリアルでは、前のレッスンとの複数の概念を組み合わせて、独自のサンプルエクスペリエンスを作成します。 旧暦モジュールアセンブリアプリケーションを作成する方法について学習します。ユーザーは、追跡したハンドを使用して旧暦モジュールパーツを取得し、旧暦モジュールを組み立てる必要があります。 Pressable ボタンを使用して配置ヒントを切り替え、エクスペリエンスをリセットして、旧暦モジュールをスペースで起動します。 今後のチュートリアルでは、このエクスペリエンスの構築を続けています。これには、空間アラインメントに Azure 空間アンカーを利用する強力なマルチユーザーユースケースが含まれます。

## <a name="objectives"></a>目標

- 前のレッスンの複数の概念を組み合わせて固有のエクスペリエンスを作成する
- オブジェクトを切り替える方法を学習する
- 押しボタンを使用して複雑なイベントをトリガーする
- 剛体の物理学と力を使用する
- ヒントの使用を調査する

## <a name="instructions"></a>手順

### <a name="configuring-the-lunar-module"></a>月着陸船の構成

このセクションでは、サンプルエクスペリエンスを作成するために必要なさまざまなコンポーネントについて説明します。

1. 基本シーンに旧暦モジュールアセンブリ prefab を追加します。 これを行うには、プロジェクト タブでロケット Launcher_Tutorial を検索します。 資産-> BaseModuleAssets-> Prefabs の prefab を見つけます。 また、2つのロケットランチャー prefabs も表示されます。1つは "チュートリアル" という名前で、もう1つは "complete" という名前です。 ロケット Launcher_Tutorial prefab を基本シーンにドラッグし、必要に応じて位置を移動します。
注: ロケット Launcher_Complete prefab は、参照用に用意された、完成したランチャーです。 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

階層内でロケット Launcher_Tutorial game オブジェクトを展開し、さらに太陰暦モジュールオブジェクトを展開すると、"x 射線" という素材を持ついくつかの子オブジェクトが見つかります。 "X 射線" のマテリアルでは、ユーザーの配置ヒントとして使用される半透明色を使用できます。 

![Lesson6](images/Lesson6_Chapter1_noteaim.PNG) Chapter1.txt については、次の図に示すように、ユーザーが対話する、太陰暦モジュールに5つの部分があります。

1.  探査車格納庫
2.  燃料タンク
3.  エネルギー セル
4.  ドッキング ポータル 
5.  外部センサー

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> 注: 基本のシーン階層に表示されるゲームオブジェクト名は、シーン内のオブジェクトの名前とは対応していません。

手順 2: 旧暦モジュールにオーディオソースを追加します。 基本のシーン階層で旧暦モジュールが選択されていることを確認し、[コンポーネントの追加] をクリックします。 オーディオソースを検索し、オブジェクトに追加します。 ここでは空白のままにして、[Spatialize] チェックボックスをオンにして、空間オーディオを有効にします。 これは、後でサウンドを再生するために使用します。

 ![Lesson6 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)  
手順 3: スクリプトの切り替えの配置ヒントを追加します。 [コンポーネントの追加] をクリックし、[配置ヒントの切り替え] を検索します。 これは、前に説明したように半透明のヒント (x 線を持つオブジェクト) をオンまたはオフにできるカスタムスクリプトです。  
![Lesson6 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)  
手順 4: 5 つのオブジェクトがあるため、game オブジェクトの配列サイズとして「5」と入力します。 5つの新しい要素が表示されます。  


![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

各半透明オブジェクトを [すべての名前 (Game Obect)] ボックスにドラッグします。
[Base Scene] の月着陸船の次のオブジェクトをドラッグします。 

•   Backpack

•   GasTank

•   Topleftbody

•   Nose

•   LeftTwirler

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

[配置ヒントの切り替え] スクリプトが構成され、ヒントをオンまたはオフにできるようになりました。

手順 5: Launch 旧暦モジュールスクリプトを追加します。 [コンポーネントの追加] ボタンをクリックし、[旧暦モジュールの起動] を検索して選択します。 このスクリプトは、旧暦モジュールを起動します。 構成されたボタンを押したときに、旧暦モジュールの固定本文コンポーネントに上位の力が追加され、モジュールが上に起動します。 屋内にいる場合は、月着陸船が天井メッシュに当たってクラッシュする可能性があります。 雲の高低がある領域にいる場合、旧暦モジュールはスペースを無制限に飛びます。 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

手順 6: 推力を調整して、旧暦モジュールが適切に起動されるようにします。 0\.01 の値を試してください。 [Rb] フィールドは空白のままにします。 Rb は固定の本体を表し、このフィールドは実行時に自動的に設定されます。

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>旧暦モジュールパーツの概要
旧暦モジュールパーツの親オブジェクトは、ユーザーが操作するオブジェクトのコレクションです。 Paretheses の名前が付いたシーンを含む Game オブジェクト名は、次の一覧に示されています。

- Backpack (燃料タンク)
- GasTank (エネルギー セル)
- TopLeftBody (探査車格納庫)
- Nose (ドッキング ポータル)
- LeftTwirler (外部センサー)

レッスン4で説明されているように、これらの各オブジェクトには操作ハンドラーがあることに注意してください。 この機能を使用すると、ユーザーはオブジェクトを取得して操作できます。 また、設定の2つのきき操作の種類が移動と回転に設定されていることにも注意してください。 このオプションは、オブジェクトの移動だけを許可し、アセンブリアプリケーションに必要な機能であるサイズを変更することはできません。
さらに、モジュールパーツを直接やり取りするためだけに、遠くの操作はオフになっています。

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

部分アセンブリデモスクリプト (上図参照) は、ユーザーがユーザーによってユーザーが旧暦モジュールに配置するオブジェクトを管理するスクリプトです。 

フィールドを配置するオブジェクトは、上の図に示すように選択されている変換です。これは、接続先のオブジェクトに関連付けられている backpack/燃料タンクです。 

近距離距離と遠く距離の設定によって、どのパーツがどこに配置されているか、または解放できるかが決まります。 たとえば、backpack/燃料タンクは、位置に合わせる前に、旧暦モジュールから離れた0.1 単位である必要があります。 [遠くの距離] 設定では、オブジェクトが旧暦モジュールからデタッチできるようになる位置が設定されます。 この場合、ユーザーの手は Backpack/燃料タンクをつかみ、再度はめ込まれないように取り外すには月着陸船から 0.2 ユニット離れた場所に引く必要があります。

ツールヒントオブジェクトはシーンのツールヒントラベルです。 オブジェクトが所定の位置にスナップされると、ラベルは無効になります。 

オーディオソースが自動的にグラブされます。 

### <a name="placement-hints-buttons"></a>配置ヒントボタン
[レッスン 2](mrlearning-base-ch2.md)では、項目の色を変更したり、プッシュ時に音を鳴らすようにしたりするためのボタンを配置および構成する方法について学習しました。 ここでは配置のヒントを切り替えるためのボタンを構成するため、これらの原則を引き続き使用します。 

目標は、ユーザーが配置ヒントボタンを押すたびに、半透明の配置ヒントが表示されるように、ボタンを構成することです。 

手順 1: 基本のシーン階層で配置ヒントオブジェクトが選択されているときに、[インスペクター] パネルの空のランタイムのみのスロットに旧暦モジュールを移動します。 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 手順 2: [関数なし] ドロップダウンリストをクリックします。 TogglePlacementHints に移動し、そのメニューの下にある ToggleGameObjects () を選択します。 ToggleGameObjects () は、ボタンが押されるたびに表示または非表示になるように配置ヒントのオンとオフを切り替えます。  
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>[リセット] ボタンの構成

場合によっては、ユーザーが誤ってオブジェクトを破棄したり、エクスペリエンスをリセットしたりすることがあります。 [リセット] ボタンをクリックすると、エクスペリエンスを再起動する機能が追加されます。 

手順 1: リセットボタンを選択します。 基本シーンでは、ResetRoundButton という名前が付けられます。 

手順 2: [インスペクター] パネルで押されたボタンの下の空のスロットに、[基本シーン] 階層の [旧暦] モジュールをドラッグします。
 ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

手順 3: [関数なし] ドロップダウンメニューを選択し、LaunchLunarModule の上にマウスポインターを移動し、[resetModule ()] を選択します。

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> 注: 既定では、BroadcastMessage は ResetPlacement に構成されていることに注意してください。 これにより、RocketLauncher_Tutorial のすべての子オブジェクトに対して ResetPlacement というメッセージがブロードキャストされます。 ResetPlacement () のメソッドを持つオブジェクトは、その位置をリセットすることによって、そのメッセージに応答します。 

### <a name="launching-the-lunar-module"></a>旧暦モジュールを起動しています
ここでは、[起動] ボタンを構成する方法について説明します。このボタンを使用すると、ユーザーはボタンをクリックして、スペースで旧暦モジュールを起動することができます。

手順 1: [起動] ボタンを選択します。 基本シーンでは、LaunchRoundButton と呼ばれます。 [インスペクター] パネルの [タッチエンド] の下にある空のスロットに、旧暦モジュールをドラッグします。
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 手順 2: [関数なし] ドロップダウンメニューを選択し、LaunchLunarModule の上にマウスポインターを移動し、[StopThruster ()] を選択します。 これにより、ユーザーが旧暦モジュールに与える推力の量が制御されます。 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)  
手順 3: ButtonPressed () の下で、空のスロットに旧暦モジュール (クリック、ホールド、ドラッグ) を追加します。 

手順 4: [関数なし] ドロップダウンメニューをクリックし、LaunchLunarModule の上にマウスポインターを移動して、[StartThruster ()] を選択します。 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)  
手順 5: 音楽がロケットの撮影時に再生されるように、旧暦モジュールに音楽を追加します。 これを行うには、[] ボタンが押された状態の次の空のスロット () に旧暦モジュールをドラッグします。

手順 6: [関数なし] ドロップダウンメニューを選択し、AudioSource の上にマウスポインターを移動して、[PlayOneShot (Audiosource)] を選択します。 MRTK に含まれているさまざまな音から自由に選択してください。 この例では、"MRTK_Gem" を使用します。
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>結論 
このアプリケーションは完全に構成されています。 ここで、[再生] をクリックすると、旧暦モジュールを完全に組み立て、ヒントを切り替えることができます。また、旧暦モジュールを起動してリセットし、再起動することもできます。
