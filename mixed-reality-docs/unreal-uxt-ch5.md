---
title: 5. ボタンの追加およびピースの位置のリセット
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアルのパート 5
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: df5ea22e7097fdd3b788ec298bc1cd78c315b585
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840401"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5.ボタンの追加およびピースの位置のリセット

このセクションでは、Mixed Reality ツールキット UX ツール プラグインの機能のデモンストレーションと、チェス アプリの機能の構築について引き続き説明します。 新しい関数を作成し、使用しているレベルからアクターへの参照をブループリントに取り込む方法を学習します。

## <a name="objectives"></a>目標

* プロジェクトにボタンを追加する
* ピースを元の位置に戻す新しい "Reset Location" 関数を作成する
* 押されたときに新しく作成された関数をトリガーするボタンをフックする

## <a name="create-a-function-to-reset-location"></a>位置をリセットする関数を作成する

1.  **WhiteKing** を開きます。 **[My Blueprint]\(マイ ブループリント\)** パネルで、 **[Functions]\(関数\)** セクションの横の [+] ボタンをクリックして新しい関数を作成します。 この関数に "Reset Location" という名前を付けます。 

2.  新しく作成した **Reset Location** ブループリントで、実行ピンをドラッグし、ブループリント グリッドの任意の場所でリリースして **SetActorRelativeTransform** ノードを呼び出します。 この関数では、アクターの親に対して相対的に変換 (位置、回転、スケール) を設定します。 この関数を使用すると、ボードが元の位置から移動した場合でもボード上のキングの位置がリセットされます。 位置が X = -26、Y = 4、Z = 0 に設定された **Make Transform** ノードを作成し、新しい相対変換入力に接続します。 

![Reset Location (位置のリセット) 関数](images/unreal-uxt/5-function.PNG)

3.  **WhiteKing** をコンパイルして保存します。 メイン ウィンドウに戻ります。 

## <a name="add-a-button"></a>ボタンを追加する

1.  **Blueprints** フォルダーに、SimpleButton をサブクラス化する新しいブループリントを作成します。 SimpleButton は、UX ツール プラグインの一部として提供される 3D ボタンのブループリント アクターです。 このボタンに "ResetButton" という名前を付け、ダブルクリックしてブループリントを開きます。 

![SimpleButton から新しいブループリントをサブクラス化する](images/unreal-uxt/5-subclass.PNG)

2.  **[コンポーネント]** パネルで、 **[PressableButton (Inherited)]\(PressableButton (継承)\)** をクリックします。 [詳細] パネルで、 **[イベント]** セクションが表示されるまでスクロールします。 **[On Button Pressed]\(ボタンが押されたとき\)** の横にある緑色のプラスのボタンをクリックします。これにより、ボタンが押されたときに呼び出される **[On Button Pressed]\(ボタンが押されたとき\)** イベントがイベント グラフに追加されます。 ここから、WhiteKing の Reset Location 関数を呼び出す必要があります。 これを行うには、まず、このレベルでの WhiteKing アクターへの参照を取得する必要があります。 

3.  **[My Blueprint]\(マイ ブループリント\)** パネルで、 **[変数]** セクションを見つけ、 **+** ボタンをクリックして新しい変数を追加します。 この変数に "WhiteKing" という名前を付けます。 [Details]\(詳細\) パネルで、 **[Variable Type]\(変数の種類\)** の横にあるドロップダウンを選択し、"WhiteKing" を検索して、 **[Object Reference]\(オブジェクト参照\)** を選択します。 最後に、 **[Instance Editable]\(インスタンス編集可能\)** の横のボックスをオンにします。 これにより、変数をメイン レベルから設定できるようになります。 

![変数を作成する](images/unreal-uxt/5-var.PNG)

4.  WhiteKing 変数を **[My Blueprint]\(マイ ブループリント\) > [Variables]\(変数\)** から Simple Button イベント グラフにドラッグします。 **[Get WhiteKing]\(WhiteKing の取得\)** を選択します。 

5.  WhiteKing の出力ピンをドラッグしてリリースし、新しいノードを配置します。 **Reset Location** 関数を選択します。 最後に、 **[On Button Pressed]\(ボタンが押されたとき\)** から出力実行ピンを **[Reset Location]** の入力実行ピンにドラッグします。 ResetButton ブループリントの **[Compile]\(コンパイル\)** と **[Save]\(保存\)** の後、メイン ウィンドウに戻ります。 

![On Button Pressed (ボタンが押されたとき) から Reset Location 関数を呼び出す](images/unreal-uxt/5-callresetloc.PNG)

6.  **SimpleButton** をビューポートにドラッグし、その位置を X = 50、Y = -25、Z = 10 に設定します。 **[Default]\(既定\)** で、WhiteKing 変数の値を **WhiteKing** に設定します。

![変数の値を設定する](images/unreal-uxt/5-buttonlevel.PNG)

これで、グラブ可能なチェス ピースとボードを備えた Mixed Reality アプリと、押されたときにピースの位置をリセットする、完全に機能するボタンが完成しました。 この時点まで完成したアプリを [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) で見つけることができます。 このチュートリアルをさらに進めて、ユーザーがボタンを押したときにボード全体がリセットされるように、チェスの残りのピースを設定してみてください。

![ビューポートの終わりのシーン](images/unreal-uxt/5-endscene.PNG)

[次のセクション: 6.デバイスまたはエミュレーターのパッケージ化およびデプロイ](unreal-uxt-ch6.md)