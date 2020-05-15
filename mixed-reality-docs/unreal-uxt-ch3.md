---
title: 3. Mixed Reality のプロジェクト設定
description: Unreal Engine 4 と Mixed Reality Toolkit UX Tools プラグインを使用して簡単なチェス アプリを構築するチュートリアルのパート 3
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality,、チュートリアル, はじめに, mrtk, uxt, UX Tools, ドキュメント
ms.openlocfilehash: b5b5e2de787279602341e60f2bfa29aa05ea9b31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840621"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3.Mixed Reality のプロジェクト設定

このセクションでは、Mixed Reality 開発用にアプリを構成するプロセスについて説明します。 

## <a name="objectives"></a>目標

* ARSessionConfig、ポーン、GameMode を使用して Mixed Reality プロジェクトを設定する方法について説明する

## <a name="configure-the-session"></a>セッションを構成する

1. コンテンツ ブラウザーで、**Content** フォルダーに戻ります。 **[新規追加] > [その他] > [Data Asset]\(データ資産\)** をクリックします。 

2. クラスに **ARSessionConfig** を選択し、 **[選択]** をクリックします。 資産に "ARSessionConfig" という名前を指定します。

![データ資産を作成する](images/unreal-uxt/3-createasset.PNG)

3. ARSessionConfig をダブルクリックして開きます。 ARSessionConfig データ資産には、空間マッピングやオクルージョンなど、便利な AR 設定が多数含まれています。 ARSessionConfig の詳細については、Unreal Engine の [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) に関するドキュメントを参照してください。 このチェス アプリでは、設定を変更する必要がないため、 **[保存]** をクリックして、メイン ウィンドウに戻ります。 

![AR セッション構成](images/unreal-uxt/3-arsessionconfig.PNG)

4. ビューポートの上のツールバーで、 **[Blueprints]\(ブループリント\) > [Open Level Blueprint]\(レベル ブループリントを開く\)** をクリックします。 レベル ブループリントは、レベル全体のグローバル イベント グラフとして機能する特別なブループリントです。 ここで AR セッションを開始して、設定した AR セッション構成がレベルの開始時に適用されるようにします。  

5. 実行ノードを **Event BeginPlay** からドラッグ アンド リリースします。 **Start AR Session** ノードを検索します。 **[Session Config]\(セッション構成\)** をクリックし、新しく作成した **ARSessionConfig** 資産を選択します。 **[コンパイル]** 、 **[保存]** の順にクリックします。 メイン ウィンドウに戻ります。

![AR セッションを開始する](images/unreal-uxt/3-startarsession.PNG)

## <a name="create-a-pawn"></a>ポーンを作成する

1.  Content フォルダーで、**DefaultPawn** から継承して新しいブループリントを作成します。 Unreal では、ポーンはゲーム内のユーザーを表します。この場合は HoloLens 2 を使います。 新しいポーンの名前を "MRPawn" に変更し、MRPawn をダブルクリックして開きます。 

![DefaultPawn から継承して新しいポーンを作成する](images/unreal-uxt/3-defaultpawn.PNG)

2.  既定では、ポーンにメッシュ コンポーネントと衝突コンポーネントが含まれています。これは、ほとんどの Unreal プロジェクトで、ユーザーに制御されるポーンは、他のコンポーネントと衝突するソリッド オブジェクトであるからです。 今回の状況では、ユーザーがポーンであるため、衝突を起こさずにホログラムを通過できるようにしたいと考えています。 [コンポーネント] パネルで、**CollisionComponent** を選択します。 [詳細] パネルで、[Collision]\(衝突\) セクションまで下にスクロールし、[Collision Presets]\(衝突のプリセット\) の横にあるドロップダウンをクリックします。 これをポーンから **[NoCollision]** に変更します。 **MeshComponent** に対しても同じ操作を行います。 ブループリントを**コンパイル**してから、**保存**します。 メイン ウィンドウに戻ります。 

![ポーンの衝突プリセットを調整する](images/unreal-uxt/3-nocollision.PNG)

## <a name="create-a-game-mode"></a>ゲーム モードを作成する

1.  コンテンツ ブラウザーの Content フォルダーで、親が **Game Mode Base** の新しいブループリントを作成します。 MRGameMode という名前を指定し、ダブルクリックして開きます。 Unreal では、ゲーム モードで、使用する既定のポーンなど、ゲームやエクスペリエンスのさまざまな設定を決定します。 

![コンテンツ ブラウザー内の MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  [詳細] パネルで、[クラス] セクションを探します。 [Default Pawn Class]\(既定のポーン クラス\) を DefaultPawn から、先ほど作成した **MRPawn** に変更します。 **[コンパイル]** 、 **[保存]** の順にクリックします。 メイン ウィンドウに戻ります。 

![既定のポーン クラスを設定する](images/unreal-uxt/3-setpawn.PNG)

3.  プロジェクト設定の最後の手順では、Unreal で MRGameMode を既定値に設定します。 **[編集] > [Projects Settings]\(プロジェクト設定\) > [Maps & Modes]\(マップ & モード\)** ([プロジェクト] セクション内) にアクセスします。 [Default Modes] \(既定のモード\) セクションで、ドロップダウンをクリックし、 **[MRGameMode]** を選択します。 その下の [Default Maps]\(既定のマップ\) セクションで、 **[EditorStartupMap]** と **[GameDefaultMap]** を **[メイン]** に変更します。 これにより、エディターを閉じて再度開くと、メイン マップが既定で選択されます。 同様に、ゲームのプレイ時は、メイン マップが、開始されるレベルになります。 

![プロジェクト設定 - マップ & モード](images/unreal-uxt/3-mapsandmodes.PNG)

[次のセクション:4.シーンを対話型にする](unreal-uxt-ch4.md)