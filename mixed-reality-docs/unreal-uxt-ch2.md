---
title: 2. プロジェクトと最初のアプリケーションの初期化
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリをビルドするためのチュートリアルのパート 2
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, 機能, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: fc85f011ff3b186f3b4b5449b4f8ec49f0b6418f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851576"
---
# <a name="2-initializing-your-project-and-first-application"></a>2.プロジェクトと最初のアプリケーションの初期化

このセクションでは、HoloLens 2 用の新しい Unreal アプリケーションの作成を開始します。 

## <a name="objectives"></a>目標

* HoloLens 開発用に Unreal を構成する
* アセットをインポートし、シーンをセットアップする

## <a name="create-a-new-unreal-project"></a>新しい Unreal プロジェクトを作成する

1. Unreal Engine を起動します。

2. **[New Project Categories]\(新規プロジェクトのカテゴリ\)** で、 **[ゲーム]** を選択して [次へ] をクリックします。 **[Blank]\(空のプロジェクト\)** テンプレートを選択して [次へ] をクリックします。 

![[Blank]\(空のプロジェクト\) テンプレートを選択する](images/unreal-uxt/2-template.PNG)

3. [Project Settings]\(プロジェクト設定\) で、 **[C++]、[Scalable 3D or 2D]\(3D または 2D に拡張可能\)、[Mobile / Tablet]\(モバイル/タブレット\)** 、 **[No Starter Content]\(スターター コンテンツを有効にしない\)** を選択します。 プロジェクトを保存する場所を選択して、 **[Create Project]\(プロジェクトを作成\)** をクリックします。 これにより、Visual Studio プロジェクト内の C++ ファイルと Unreal エディターが表示されます。 

![最初のプロジェクト設定](images/unreal-uxt/2-project-settings.PNG)

4. 左上隅の **[編集] > [プラグイン]** に移動します。 [Augmented Reality]\(拡張現実\) で、 **[HoloLens]** プラグインを有効にするボックスをオンにします。 [Virtual Reality]\(仮想現実\) セクションまで下にスクロールして、 **[Microsoft Windows Mixed Reality]** プラグインを有効にするボックスをオンにします。 HoloLens 2 の開発には、両方のプラグインが必要です。 エディターを再起動します。 

![プラグイン](images/unreal-uxt/2-plugins.PNG)

5. 左上隅の **[ファイル] > [New Level]\(新規レベル\)** に移動します。 **[Empty Level]\(空のレベル\)** を選択します。 この時点では、ビューポートの既定のシーンは空です。

6. 左側の [モード] パネルの [基本] タブにある PlayerStart をドラッグ アンド ドロップします。アプリの起動時にユーザーを原点から開始させるために、右側の [詳細] パネルで、位置を X = 0、Y = 0、Z = 0 に設定します。

![PlayerStart を表示したビューポート](images/unreal-uxt/2-playerstart.PNG)

7. **[Cube]\(キューブ\)** を [モード] パネルの [基本] タブからビューポートにドラッグします。 [詳細] パネルで、位置を X = 50、Y = 0、Z = 0 に設定して、キューブをプレーヤーの開始位置から 50 cm 離して配置します。 既定のキューブは非常に大きいため、キューブの [Scale]\(スケール\) を (0.2, 0.2, 0.2) に変更します。 

8. シーンにライトを追加しない限り、キューブを表示することはできません。 [モード] パネルの **[Lights]\(ライト\)** タブに切り替えて、**Directional Light** をシーンの PlayerStart の上にドラッグします。

![ライトが追加されたビューポート](images/unreal-uxt/2-light.PNG)

9.  ツールバーの **[Play]\(プレイ\)** ボタンを押して、ビューポートにキューブを表示します。 **Esc** キーを押して、レベルを停止します。 

![ビューポート内のキューブ](images/unreal-uxt/2-cube.PNG)

10. レベルを保存しましょう。 左上隅の **[ファイル] > [Save Current]\(現在のレベルを保存\)** をクリックします。 レベルに "Main" という名前を付けて、 **[保存]** をクリックします。 

## <a name="set-up-a-chess-scene"></a>チェス シーンを設定する

1. コンテンツ ブラウザーで、[Add New]\(新規追加\) の下にあるアイコンをクリックして、ソース パネルを表示します。 **[Add New]\(新規追加\) > [New Folder]\(新規フォルダ\)** をクリックして、フォルダーに "ChessAssets" という名前を付けます。 このフォルダーをダブルクリックして、移動します。 ここに、チェス セットの 3D アセットをインポートします。

![ソース パネルの表示と非表示](images/unreal-uxt/2-showhidesources.PNG)

2. アセットの zip ファイルを [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) からダウンロードします。 このファイルには、チェス盤とチェス セットの 3D モデルが含まれています。 このファイルを解凍します。

3. コンテンツ ブラウザーの上部にある **[インポート]** をクリックします。 解凍したばかりのフォルダーに移動して、その中のすべての項目を選択します。 このフォルダーには、チェス盤とチェスの駒の 3D オブジェクト メッシュである FBX ファイルと、チェス盤と駒のマテリアルの作成に使用するテクスチャ マップである TGA ファイルが含まれています。 **[開く]** をクリックします。 

4. [FBX Import Options]\(FBX インポート オプション\) ウィンドウが表示されます。 **[Material]\(マテリアル\)** セクションで、 **[Material Import Method]\(マテリアルのインポート方法\)** を **[Do Not Create Material]\(マテリアルを作成しない\)** に変更します。 次に、 **[Import All]\(すべてインポート\)** をクリックします。

![FBX インポート オプション](images/unreal-uxt/2-nocreatemat.PNG)

5. [コンテンツ] フォルダーに戻って、**Blueprints** という名前の新しいフォルダーを作成します。 ここに、すべてのブループリントを格納します。ブループリントは、新しい種類のアクターやスクリプト レベルのイベントを作成するためのノードベースのインターフェイスを提供する特別なアセットです。 

6. **[Blueprints]\(ブループリント\)** フォルダーをダブルクリックして、内部に移動し、[Content Browser]\(コンテンツ ブラウザー\) を右クリックして、 **[Blueprint Class]\(ブループリント クラス\)** を選択します。 **[Actor]\(アクター\)** をクリックして、新しいブループリントに "Board" という名前を付けます。 Board をダブルクリックして開きます。 

![ブループリントの親クラスを選択する](images/unreal-uxt/2-bpparent.PNG)

![新しい Board ブループリント](images/unreal-uxt/2-bpboard.PNG)

7. ブループリント エディターで、[コンポーネント] パネルに移動し、 **[Add Component]\(コンポーネントの追加\) > [シーン]** の順にクリックします。 新しく作成したシーンに "Root" という名前を付け、Root をクリックして、DefaultSceneRoot の上にドラッグします。 これにより、既定のシーンがルートに置き換えられて、ビューポートで球が削除されます。 

![ルートを置き換える](images/unreal-uxt/2-root.PNG)

8. **[Add Component]\(コンポーネントの追加\)** を再度クリックし、今度は **[Static Mesh]\(スタティック メッシュ\)** を選択します。 新しいスタティック メッシュに "SM_Board" という名前を付けます。 

![スタティック メッシュの追加](images/unreal-uxt/2-sm-board.PNG)

9. **[詳細]** パネルで **[Static Mesh]\(スタティック メッシュ\)** セクションを見つけて、ドロップダウンをクリックします。 **ChessBoard** を選択します。 

![ビューポート内のボード メッシュ](images/unreal-uxt/2-sm-board-view.PNG)

10. **[詳細]** パネルのままで、 **[Materials]\(マテリアル\)** セクションを見つけて、ドロップダウンをクリックします。 **[Create New Asset]\(アセットの新規作成\)** で、 **[Material]\(マテリアル\)** を選択します。 このアセットに **M_ChessBoard** という名前を付けて、**ChessAssets**フォルダーに保存します。 

![新しいマテリアルを作成する](images/unreal-uxt/2-newmat.PNG)

11. M_ChessBoard ドロップダウンの横に表示された四角形をダブルクリックして、新しく作成した M_ChessBoard マテリアルを開きます。 マテリアル エディターで右クリックして、 **[Texture Sample]\(テクスチャ サンプル\)** ノードを検索します。 **[詳細]** パネルの **[Material Expression Texture Base]\(マテリアル式テクスチャ ベース\)** セクションでドロップダウンをクリックして、**ChessBoard_Albedo** を選択します。 最後に、 **[RGB]** 出力ピンを **M_ChessBoard** の [Base Color]\(基本色\) ピンにドラッグします。 

![基本色を設定する](images/unreal-uxt/2-boardalbedomat.PNG)

12. 同じ手順をさらに 4 回実行して、**ChessBoard_AO** テクスチャ サンプルを **[Ambient Occlusion]\(アンビエント オクルージョン\)** ピンに、**ChessBoard_Metal** テクスチャ サンプルを **[Metallic]\(メタリック\)** ピンに、**ChessBoard_Normal** テクスチャ サンプルを **[Normal]\(ノーマル\)** ピンに、**ChessBoard_Rough** テクスチャ サンプルを **[Roughness]\(ラフネス\)** ピンにリンクします。 **[Save]** (保存) をクリックします。 

![残りのテクスチャを接続する](images/unreal-uxt/2-boardmat.PNG)

13. **Board** ブループリントに戻ります。 作成したばかりのマテリアルがブループリントに適用されていることがわかります。 チェス盤をシーンに配置した後、それが適切なサイズで適切な位置に配置されるようにするには、チェス盤の **[Scale]\(スケール\)** を (0.05, 0.05, 0.05) に変更し、 **[回転]** を Z = 90 に変更します。 上部のツールバーで **[コンパイル]** 、 **[保存]** の順にクリックします。 メイン ウィンドウに戻ります。 

![マテリアルが適用されたチェス盤](images/unreal-uxt/2-chessboard.PNG)

14. 次に、キューブを削除して、それを新しく作成した Board アクターに置き換えましょう。 **[World Outliner]\(ワールド アウトライナー\)** で、 **[Cube]\(キューブ\) を右クリックして、[編集]、[削除]** の順にクリックします。 Board をコンテンツ ブラウザーからビューポートにドラッグします。 チェス盤の位置を X = 80、Y = 0、Z = -20 に設定します。 

15. **[Play]\(プレイ\)** ボタンをクリックして、新しいチェス盤をレベルに表示します。 **Esc** キーを押してエディターに戻ります。 

16. 次に、チェス盤の作成と同じ手順に従って、チェスの駒を作成します。ただし、今度は、チェスの駒のメッシュとマテリアルを選択します。

    a) コンテンツ ブラウザーの [ブループリント] フォルダーに移動して、アクター型の新しいブループリント クラスを作成します。 このアクターに "WhiteKing" という名前を付けます。

    b) WhiteKing をダブルクリックして開きます。 "Root" という名前の新しいシーンを追加し、それを使用して DefaultSceneRoot を置き換えます。 

    c) "SM_King" という名前の新しいスタティック メッシュ コンポーネントを追加します。 [詳細] パネルで、 **[Static Mesh]\(スタティック メッシュ\)** を **Chess_King** に設定し、 **[Material]\(マテリアル\)** を、**M_ChessWhite**という名前の新しいマテリアルに設定します。 

    d) 新しい **M_ChessWhite**マテリアルを開いて、関連テクスチャをその対応するマテリアル入力に接続します。 

    ![チェスのキングのマテリアルを作成する](images/unreal-uxt/2-chesskingmat.PNG)

    e) **WhiteKing** ブループリントに戻って、 **[Scale]\(スケール\)** を (0.05, 0.05, 0.05) に、 **[回転]** を Z = 90 に変更します。

    f) ブループリントをコンパイルして保存した後、メイン ウィンドウに戻ります。 

17. WhiteKing をビューポートにドラッグします。 **[World Outliner]\(ワールド アウトライナー\)** で、WhiteKing を Board にドラッグします。これにより、WhiteKing は Board の子になります。 

![[World Outliner]\(ワールド アウトライナー\)](images/unreal-uxt/2-child.PNG)

18. **[詳細]** パネルの **[Transform]\(トランスフォーム\)** で、WhiteKing の **[Location]\(位置\)** を X = -26、Y = 4、Z = 0 に設定します。

19. **[Play]\(プレイ\)** をクリックして、レベルを表示します。 **Esc** キーを押して終了します。 

[次のセクション: 3.Mixed Reality 用のプロジェクト設定](unreal-uxt-ch3.md)