---
title: 4. シーンを対話型にする
description: Unreal Engine 4 と Mixed Reality Toolkit UX Tools プラグインを使用して簡単なチェス アプリを構築するチュートリアルのパート 4
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality,、チュートリアル, はじめに, mrtk, uxt, UX Tools, ドキュメント
ms.openlocfilehash: 17f7ab1c1126c47e5ac6388d125d45cf3f2c2d87
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851552"
---
# <a name="3-making-your-scene-interactive"></a>3.シーンを対話型にする

このセクションでは、オープン ソースの Mixed Reality Toolkit UX Tools プラグインについて説明します。このプラグインには、シーンを簡単に対話型にするための一連のツールが用意されています。 このセクションを終えると、チェスの駒がユーザー入力に応答するようになります。 

## <a name="objectives"></a>目標

* プロジェクトに Mixed Reality Toolkit UX Tools プラグインを含める
* ハンド インタラクション アクターを指先に追加する
* マニピュレーターを作成してチェス ボードと駒にアタッチする 
* 入力シミュレーションを使用してプロジェクトを検証する

## <a name="download-the-mixed-reality-toolkit-ux-tools-plugin"></a>Mixed Reality Toolkit UX Tools プラグインをダウンロードする

1.  [UX Tools GitHub リポジトリ](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)から、MRTK UX Tools プラグインの最新リリースをクローンまたはダウンロードして解凍します

2.  チェス プロジェクトのルート フォルダーに、"Plugins" という名前の新しいフォルダーを作成します。 解凍した UXTools プラグインをこのフォルダーにコピーします。 Unreal エディターを再起動します。 

![プロジェクト プラグイン フォルダーを作成する](images/unreal-uxt/4-plugins.PNG)

3.  再起動後、ソース パネルに UXTools プラグイン コンテンツが表示されない場合は、 **[View Options]\(表示オプション\) > [Show Plugin Content]\(プラグイン コンテンツの表示\)** をクリックしてください。 UXTools プラグインでは、Content フォルダー内に、ポインター、入力シミュレーション、および単純なボタンが提供され、C++ Classes フォルダー内に、関数別のサブフォルダーが提供されます。  

![プラグイン コンテンツを表示する](images/unreal-uxt/4-showplugincontent.PNG)

## <a name="spawn-hand-interaction-actors"></a>ハンド インタラクション アクターを生成する

1.  まず、MRPawn からハンド インタラクション アクターを生成します。1) ポーンの人差し指の先にカーソルを設定して、MRPawn を視覚化できます。2) ポーンから多関節ハンド入力イベントを提供できます (これにより、アクターを直接操作できます)。3) 手の平から伸びるハンド レイを使って、遠隔インタラクション入力イベントを提供できます。 **MRPawn** ブループリントを開き、 **[Event Graph]\(イベント グラフ\)** に移動します。 

2.  Event BeginPlay から実行ピンをドラッグ アンド リリースして、新しいノードを配置します。 **Spawn Actor from Class** ノードを選択します。 **[クラス]** ピンの横にあるドロップダウンをクリックし、**Uxt ハンド インタラクション アクター**を検索します。 SpawnActor Uxt Hand Interaction ノードから実行ピンをドラッグ アンド リリースし、Uxt Hand Interaction Actor クラスに含まれる **Set Hand** 関数を検索します。 SpawnActor ノードの戻り値を Set Hand ノードの [ターゲット] ピンに接続して、ハンド インタラクショ ンアクターの手を **[左]** に設定します。 もう 1 つの **Uxt ハンド インタラクション アクター**を生成します。今回は、手を **[右]** に設定します。これにより、イベントが開始されると、Uxt ハンド インタラクション アクターがそれぞれの手で生成されます。 

![Uxt ハンド インタラクション アクターを生成する](images/unreal-uxt/4-spawnactor.PNG)

3.  次に、Uxt ハンド インタラクション アクターに、最初の変換 (ここで生成を行う) と所有者を提供する必要があります。 **Spawn Transform** ピンの 1 つからピンをドラッグ アンド リリースして、新しいノードを配置します。 **Make Transform** ノードを検索します。 最初の変換は実際には問題ではありません。というのは、ハンド インタラクション アクターでは、表示されるとすぐに作成した手にジャンプするからです (作成済みのコードが UX Tools プラグイン内に用意されています)。それ以外の場合は、表示されなくなります。 ただし、SpawnActor 関数では、コンパイラ エラーを回避するために入力として変換が必要なため、Make Transform の既定値はそのままにします。 Make Transform の**戻り値**を、もう片方の手のインタラクション アクターの Spawn Transform にもドラッグします。 

4.  両方の SpawnActor ノードの下部にある**下矢印**をクリックして、 **[所有者]** ピンを表示します。 **[所有者]** ピンの 1 つからピンをドラッグ アンド リリースして、新しいノードを配置します。 "Self" を検索し、**Get a reference to self** 変数を選択します。 Self オブジェクト参照ノードともう一方のハンド インタラクション アクターの [所有者] ピンの間にもリンクを作成します。 ブループリントが読みやすくなるようにノードを自由にドラッグします。 **コンパイル**と**保存**を行って、メイン ウィンドウに戻ります。 

![Uxt ハンド インタラクション アクターのセットアップを完了する](images/unreal-uxt/4-fingerptrs.PNG)

MRTK UX Tools プラグインに用意されているハンド インタラクション アクターの詳細については、公式の[ドキュメント](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html)を参照してください。

## <a name="attach-manipulators"></a>マニピュレーターをアタッチする

1.  次に、マニピュレーターをチェス ボードとキング アクターにアタッチします。 マニピュレーターは、多関節ハンド入力に応答するコンポーネントであり、つかむ、回転する、変換することができます。マニピュレーターの変換をアクターの変換に適用すると、アクターを直接操作することができます。 

2.  ボードのブループリントを開きます。 **[コンポーネント]** パネルで、 **[コンポーネントの追加]** をクリックし、**Uxt 汎用マニピュレーター**を検索します。 [詳細] パネルには **[Generic Manipulator]\(汎用マニピュレーター\)** というセクションがあり、片手または両手の操作、回転モード、スムージングを有効にするかどうかを設定できます。 好きなモードを自由に選択して、ボードを**コンパイル**し、**保存**します。 

![汎用マニピュレーターを追加する](images/unreal-uxt/4-addmanip.PNG)

![モードを設定する](images/unreal-uxt/4-setrotmode.PNG)

3.  WhiteKing アクターについて上記の手順を繰り返します。

MRTK UX Tools プラグインに用意されているマニピュレーター コンポーネントの詳細については、公式の[ドキュメント](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html)を参照してください。

## <a name="test-out-your-scene-with-simulated-hands"></a>シミュレートされた手を使ってシーンをテストする

1.  メイン ウィンドウで **[プレイ]** を押します。 MRTK UX Tools プラグインから 2 つのメッシュ ハンドが提供され、それぞれの手の平からハンド レイが伸びているのを確認します。 

![ビューポート内のシミュレートされた手](images/unreal-uxt/4-handsim.PNG)

2.  **右手**を制御するには、**左 Alt** ボタンを押したままにします。 マウスを動かして手を動かします。 **マウス ホイール**を使用してスクロールして、手を**前方**または**後方**に移動します。 左マウスをクリックして**ピンチ**、マウスの中央ボタンをクリックして**指さし**を行います。

3.  **左手**を制御するには、**左 Shift** ボタンを押したままにします。 左手を移動するためのコントロールは、右側のコントロールと同じです。 

4.  ここで、シミュレートされた手を使用して、チェスの白キングを手に取り、移動して、置いてみましょう。 ボードを操作することもできます。 近接インタラクションと遠隔インタラクションの両方を試してみてください。手がボードとキングを直接つかめる位置まで近づくと、ハンド レイが消え、人差し指の先が指カーソルに置き換わります。 

MRTK UX Tools プラグインに用意されているシミュレートされた手の機能の詳細については、公式の[ドキュメント](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html)を参照してください。

[次のセクション:5.ボタンの追加およびピースの位置のリセット](unreal-uxt-ch5.md)