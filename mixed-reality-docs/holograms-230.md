---
title: MR 空間 230 - 空間マッピング
description: このコーディング空間マッピングの概念の詳細については、Unity、Visual Studio および HoloLens の使用に関するチュートリアルに従います。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit unity、academy、チュートリアル、空間マッピング、画面の再構築、メッシュ
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993559"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>MR 空間 230:空間マッピング

[空間マッピング](spatial-mapping.md)ホログラム環境に関する指示することによって、現実の世界と仮想世界をまとめて結合します。 MR 空間 230 (プロジェクト プラネタリウム用) で説明する方法。

* 開発用コンピューターに、HoloLens の環境と転送データをスキャンします。
* シェーダーを調査し、自分のスペースを視覚化するために使用する方法について説明します。
* メッシュの処理を使用して単純な平面に部屋メッシュに分解します。
* 学習した配置の手法よりも高度[MR 基本 101](holograms-101.md)ホログラムを環境に配置できる場所についてのフィードバックを提供します。
* 遮蔽効果、探索、ホログラムが現実世界のオブジェクトの背後にあると、表示できるようにも、x 線画像のビジョンを!

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 空間 230:空間マッピング</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>開始前の作業

### <a name="prerequisites"></a>前提条件

* 正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。
* 基本的なC#プログラミング機能。
* 完了する必要があります[MR 基本 101](holograms-101.md)します。
* HoloLens デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。

### <a name="project-files"></a>プロジェクト ファイル

* ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip)プロジェクトに必要です。 Unity 2017.2 またはそれ以降が必要です。
  * Unity 5.6 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)します。
  * Unity 5.5 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)します。
  * Unity 5.4 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)します。
* 解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。

>[!NOTE]
>をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)します。

### <a name="notes"></a>メモ

* 無効にする Visual Studio のニーズに「マイ コードのみを有効化」(*unchecked*) [ツール] > オプション >、コードにブレークポイントをヒットするためにデバッグします。

## <a name="unity-setup"></a>Unity のセットアップ

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* 開始**Unity**します。
* 選択**新規**新しいプロジェクトを作成します。
* プロジェクトに名前を**プラネタリウム用**します。
* いることを確認、 **3D**設定を選択します。
* クリックして**プロジェクトを作成する**します。
* Unity が起動したらに移動して**編集 > プロジェクトの設定 > Player**します。
* **インスペクター**パネルで検索し、緑色**Windows ストア**アイコン。
* 展開**他の設定**します。
* **レンダリング** セクションで、チェック、**仮想現実サポート**オプション。
* いることを確認**Windows Holographic**の一覧に表示される**仮想現実 Sdk**します。 そうでない場合は、選択、 **+** 一覧の下部にあるボタンをクリックし、選択**Windows Holographic**します。
* 展開**公開設定**します。
* **機能**セクションで、次の設定を確認します。
    * internetClientServer
    * privateNetworkClientServer
    * マイク
    * SpatialPerception
* 移動して**編集 > プロジェクトの設定 > 品質**
* **インスペクター**パネルの [Windows ストア] アイコンの下の 'Default' の行の黒のドロップダウン矢印とする既定の設定を変更する**Very Low**します。
* 移動して**資産 > パッケージのインポート > カスタム パッケージ**します。
* 移動し、 **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting**フォルダー。
* をクリックして**Planetarium.unitypackage**します。
* **[開く]** をクリックします。
* **Unity パッケージのインポート**ウィンドウが表示されます をクリックして、**インポート**ボタンをクリックします。
* このプロジェクトを完了する必要があります。 その資産のすべてをインポートする Unity を待ちます。
* **階層**パネルで、削除、 **Main Camera**します。
* **プロジェクト**パネル、 **HoloToolkit-SpatialMapping-230\Utilities\Prefabs**フォルダー、検索、 **Main Camera**オブジェクト。
* ドラッグ アンド ドロップ、 **Main Camera**にプレハブ、**階層**パネル。
* **階層**パネルで、削除、**指向性光**オブジェクト。
* **プロジェクト**パネル、**ホログラム**フォルダー、検索、**カーソル**オブジェクト。
* ドラッグ アンド ドロップ、**カーソル**にプレハブ、**階層**します。
* **階層**パネルで、**カーソル**オブジェクト。
* **インスペクター**パネルで、をクリックして、**レイヤー**ドロップダウンを選択します**レイヤーを編集しています.**.
* 名前**ユーザー層 31**として"**SpatialMapping**"。
* 新しいシーンを保存します。**ファイル > としてシーンを保存しています.**
* クリックして**新しいフォルダー**フォルダーの名前と**シーン**します。
* ファイルに名前を"**プラネタリウム用**"で保存し、**シーン**フォルダー。

## <a name="chapter-1---scanning"></a>第 1 章 - スキャン

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**目標**
* SurfaceObserver、および設定への影響を経験する方法とパフォーマンスについて説明します。
* スキャンの部屋のメッシュを収集するエクスペリエンスのルームを作成します。

**手順**
* **プロジェクト**パネル**HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs**フォルダー、検索、 **SpatialMapping** prefab します。
* ドラッグ アンド ドロップ、 **SpatialMapping**にプレハブ、**階層**パネル。

**ビルドおよび展開 (パート 1)**
* Unity では、次のように選択します。**ファイル > Build Settings**します。
* クリックして**開くシーンを追加**を追加する、**プラネタリウム用**シーンをビルドします。
* 選択**ユニバーサル Windows プラットフォーム**で、**プラットフォーム**を一覧表示し、クリックして**スイッチ プラットフォーム**します。
* 設定**SDK**に**ユニバーサル 10**と**UWP ビルドの種類**に**D3D**します。
* 確認**UnityC#プロジェクト**します。
* **[Build]** をクリックします。
* 作成、**新しいフォルダー** "App"という名前です。
* 1 回のクリック、**アプリ**フォルダー。
* キーを押して、**フォルダーの選択**ボタンをクリックします。
* Unity が完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。
* ダブルクリックして、**アプリ**フォルダーを開きます。
* ダブルクリックして**Planetarium.sln** Visual Studio でプロジェクトを読み込みます。
* Visual Studio で、上部のツールバーを使用して構成を変更する**リリース**します。
* 変更するためのプラットフォーム**x86**します。
* ' ローカル コンピューター] の右側の下矢印をクリックし、[**リモート マシン**します。
* 入力[デバイスの IP アドレス](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network)アドレス フィールドし、する認証モードを変更する**ユニバーサル (暗号化されていないプロトコル)** します。
* クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。
* ウォッチ、**出力**パネルの Visual Studio でのビルドと配置状態。
* アプリがデプロイされると、室内をについて説明します。 黒と白のワイヤー フレームのメッシュに覆わ周囲の画面が表示されます。
* 環境をスキャンします。 必ず、壁、天井、フロアを見てください。

**ビルドおよび展開 (パート 2)**

これで空間マッピングに与える影響についてパフォーマンスを見てみましょう。
* Unity では、次のように選択します。**ウィンドウ > Profiler**します。
* クリックして**Profiler の追加 > GPU**します。
* クリックして**Active Profiler > <Enter IP>** します。
* 入力、 **IP アドレス**HoloLens の。
* **[接続]** をクリックします。
* フレームのレンダリングに GPU の所要時間をミリ秒数を確認します。
* デバイスで実行されているアプリケーションを停止します。
* Visual Studio に戻り、開く**SpatialMappingObserver.cs**します。 これは、アセンブリ CSharp (ユニバーサル Windows) プロジェクトの HoloToolkit\SpatialMapping フォルダーに表示されます。
* 検索、 **Awake()** 関数は、し、次のコード行を追加します。**TrianglesPerCubicMeter 1200; を =**
* お使いのデバイスにプロジェクトを再デプロイし、**プロファイラーを再接続**します。 フレームのレンダリング時間 (ミリ秒) の数の変更を確認します。
* デバイスで実行されているアプリケーションを停止します。

**保存して Unity で読み込む**

最後に、みましょう、部屋のメッシュを保存し、Unity に読み込みます。
* Visual Studio に戻り、削除、 **TrianglesPerCubicMeter**で追加した行、 **Awake()** 前のセクションの中に機能します。
* デバイスにプロジェクトを再デプロイします。 私たちは現在実行されてで**500**立方メーターごとの三角形です。
* ブラウザーを開きに移動する、HoloLens の ip アドレスの入力、 **Windows Device Portal**します。
* 選択、 **3D 表示**左側のパネルのオプション。
* **再構築のサーフェス**選択、**更新**ボタン。
* 表示ウィンドウに表示される、HoloLens のスキャンが完了する領域をご覧ください。
* 部屋のスキャンを保存するキーを押して、**保存**ボタンをクリックします。
* 開く、**ダウンロード**ルームが保存されたモデルを見つけてフォルダー **SRMesh.obj**します。
* コピー **SRMesh.obj**を**資産**Unity プロジェクトのフォルダー。
* Unity では、選択、 **SpatialMapping**オブジェクト、**階層**パネル。
* 検索、**オブジェクトのサーフェイスのオブザーバー (スクリプト)** コンポーネント。
* 右側に円をクリックして、**ルーム モデル**プロパティ。
* 検索し、選択、 **SRMesh**オブジェクトし、ウィンドウを閉じます。
* いることを確認、**ルーム モデル**プロパティ、**インスペクター**パネルに設定されています**SRMesh**します。
* キーを押して、**再生**Unity のプレビュー モードを開始するボタンをクリックします。
* SpatialMapping コンポーネントは、Unity で使用することができます、部屋の保存されたモデルから、メッシュを読み込まれます。
* 切り替える**シーン**ワイヤー フレーム シェーダーで表示されるルーム モデルのすべてを表示するビュー。
* キーを押して、**再生**プレビュー モードを終了するには、もう一度ボタンをクリックします。

**注:** Unity では、プレビュー モードを入力すること、次回保存ルーム メッシュ既定で読み込まれます。

## <a name="chapter-2---visualization"></a>第 2 章 - 視覚エフェクト

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**目標**
* シェーダーの基本について説明します。
* 環境を視覚化します。

**手順**
* Unity の**階層**パネルで、 **SpatialMapping**オブジェクト。
* **インスペクター**パネルで、検索、**空間マッピング マネージャー (スクリプト)** コンポーネント。
* 右側に円をクリックして、**画面マテリアル**プロパティ。
* 検索し、選択、 **BlueLinesOnWalls**マテリアルと、ウィンドウを閉じます。
* **プロジェクト**パネル**シェーダー**フォルダーをダブルクリックして、 **BlueLinesOnWalls**を Visual Studio でシェーダーを開きます。
* これは、簡単なピクセル (頂点のフラグメントを)、次のタスクを実行するには、シェーダー。
    1. ワールド空間には、頂点の位置を変換します。
    2. 頂点の通常ピクセルが垂直方向であるかどうかを確認します。
    3. レンダリングのピクセルの色を設定します。

**構築し、デプロイ**
* Unity とキーを押してに戻る**再生**プレビュー モードを入力します。
* 青い線は、ルーム メッシュ (これは、保存済みのスキャン データから自動的に読み込まれます) のすべての垂直画面に表示されます。
* 切り替えて、**シーン** タブを部屋の表示を調整および Unity での部屋全体、メッシュの表示方法を参照してください。
* **プロジェクト**パネルで、検索、**資料**フォルダーと選択、 **BlueLinesOnWalls**マテリアル。
* 一部のプロパティを変更して、Unity エディターで変更の表示方法を参照してください。
    * **インスペクター**パネルで、調整、 **LineScale**線が太くまたは幅が狭いほどを表示するのには値。
    * **インスペクター**パネルで、調整、 **LinesPerMeter**各壁に表示される行の数を変更する値。
* クリックして**再生**プレビュー モードを終了するには、もう一度です。
* ビルド、HoloLens に展開し、実際のサーフェスにレンダリング シェーダーを表示する方法を確認します。

Unity は、素材のプレビューの良い仕事をするが、常に、デバイスでのレンダリングをチェック アウトすることをお勧めします。

## <a name="chapter-3---processing"></a>第 3 章 - 処理

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**目標**
* アプリケーションで使用するための空間マッピング データを処理するための手法について説明します。
* 平面を見つけて、三角形を削除する空間のマッピング データを分析します。
* ホログラムを配置するためには、平面を使用します。

**手順**
* Unity の**プロジェクト**パネル、**ホログラム**フォルダー、検索、 **SpatialProcessing**オブジェクト。
* ドラッグ アンド ドロップ、 **SpatialProcessing**オブジェクトを**階層**パネル。

SpatialProcessing プレハブには、空間のマッピング データを処理するためのコンポーネントが含まれます。 **SurfaceMeshesToPlanes.cs**見つけて平面空間マッピング データに基づいて生成されます。 平面を壁、フロア、シーリングを表すアプリケーションで使用します。 このプレハブも含まれています。 **RemoveSurfaceVertices.cs**空間マッピング メッシュから頂点を削除することができます。 これは、メッシュ内の穴を作成または削除 (平面は、代わりに使用できる) ためには必要なくなりましたされる余分な三角形に使用できます。
* Unity の**プロジェクト**パネル、**ホログラム**フォルダー、検索、 **SpaceCollection**オブジェクト。
* ドラッグ アンド ドロップ、 **SpaceCollection**オブジェクトを**階層**パネル。
* **階層**パネルで、 **SpatialProcessing**オブジェクト。
* **インスペクター**パネルで、検索、**プレイ領域マネージャー (スクリプト)** コンポーネント。
* ダブルクリックして**PlaySpaceManager.cs** Visual Studio で開きます。

PlaySpaceManager.cs には、アプリケーション固有のコードが含まれています。 機能は、次の動作を有効にするには、このスクリプトを追加します。
1. スキャンの時間制限 (10 秒) を超えた後空間マッピング データの収集を停止します。
2. 空間マッピング データを処理します。
    1. 平面 (壁、フロア、シーリングなど) として、世界中の単純な表現を作成するのにには、SurfaceMeshesToPlanes を使用します。
    2. RemoveSurfaceVertices を使用すると、面の境界内にある表面の三角形を削除します。
3. 世界でホログラムのコレクションを生成し、ユーザーに近い壁面と床面の平面上に配置します。

PlaySpaceManager.cs でマークされているコーディングの練習を完了またはスクリプトを次の完成版ソリューションを置き換え。

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

**構築し、デプロイ**
* キーを押して、HoloLens、展開する前に、**再生**再生モードに切り替わる Unity でボタンをクリックします。
* ルーム メッシュがファイルから読み込まれた後は、空間マッピング メッシュで処理を開始する前に 10 秒間待機します。
* 処理が完了したら、面は床、壁、ceiling などを表す表示されます。
* 結局、平面の発見された、太陽系の床面のカメラの近くのテーブルに表示されることがわかります。
* 2 つのポスターがすぎるの壁、カメラの近くに表示されます。 切り替えて、**シーン**タブに表示されない場合**ゲーム**モード。
* キーを押して、**再生**再生モードを終了するには、もう一度ボタンをクリックします。
* 構築し、通常どおり、HoloLens にデプロイします。
* スキャンおよび完了する空間のマッピング データの処理を待ちます。
* 平面が表示されたら、世界では、太陽系とポスターを見つけようとします。

## <a name="chapter-4---placement"></a>第 4 章 - 配置

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**目標**
* ホログラムがサーフェイス上に収まるかどうかを決定します。
* ホログラムを画面に収まるできる/できない場合は、ユーザーにフィードバックを提供します。

**手順**
* Unity の**階層**パネルで、 **SpatialProcessing**オブジェクト。
* **インスペクター**パネルで、検索、**平面に表面メッシュ (スクリプト)** コンポーネント。
* 変更、**描画面**プロパティを**Nothing**選択を解除します。
* 変更、**描画面**プロパティを**壁**、壁平面のみが表示されるようにします。
* **プロジェクト**パネル、**スクリプト**フォルダーをダブルクリックして、 **Placeable.cs** Visual Studio で開きます。

**Placeable**スクリプトは、平面の検索が完了した後に作成されるポスターとプロジェクションのボックスに既にアタッチされています。 すべてを行う必要がありますが、いくつかのコードをコメント解除し、このスクリプトは、以下を実現します。
1. ホログラムが中心境界のキューブの 4 つの角からレイキャストによって、サーフェイス上に収まるかどうかを決定します。
2. サーフェスの法線でフラッシュ待つホログラムの十分な滑らかな判断を確認してください。
3. 境界の周囲に配置されている中には、実際のサイズを表示するホログラム キューブを表示します。
4. シャドウ/背後の下に floor/壁に配置される場所を表示するホログラムをキャストします。
5. 可能な場合、画面、または緑にホログラムを配置できませんがある場合は、赤、として影をレンダリングします。
6. アフィニティを使用している画面の種類 (水平または垂直) と連携させるホログラムの向きを変更します。
7. ジャンプまたはスナップ動作を回避するために選択した画面で、ホログラムがスムーズに配置します。

コーディングの練習を下のすべてのコードのコメントを解除またはで完了したこのソリューションを使用して、 **Placeable.cs**:

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

**構築し、デプロイ**
* 同様に、プロジェクトをビルドし、HoloLens を展開します。
* スキャンおよび完了する空間のマッピング データの処理を待ちます。
* 太陽系を確認したら、下にある投影ボックス見つめます、周囲に移動して選択ジェスチャを実行します。 プロジェクション ボックスを選択したら、外接するキューブは、プロジェクション ボックス表示にされます。
* 部屋に別の場所を見つめますにヘッドを移動します。 プロジェクションのボックスは、視線の先で従う必要があります。 プロジェクションのボックスの下の影が赤に変わり場合、は、その画面でホログラムを配置することはできません。 プロジェクションのボックスの下の影が緑色に変わり場合、は、もう 1 つ選択ジェスチャを実行することによって、ホログラムを配置できます。
* 検索し、新しい場所に移動する壁 holographic のポスターのいずれかを選択します。 Floor、ceiling のポスターを配置することはできず、ラベルを保持する各壁を正しい方向を移動するように注意してください。

## <a name="chapter-5---occlusion"></a>第 5 章 - 重なり

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**目標**
* ホログラムが空間マッピング メッシュによってオクルー ジョンかどうかを決定します。
* 楽しいを実現するために異なるオクルー ジョン手法を適用効果。

**手順**

最初に、ここでは現実の世界を occluding せず他ホログラムがメッシュの空間マッピングを許可します。
* **階層**パネルで、 **SpatialProcessing**オブジェクト。
* **インスペクター**パネルで、検索、**プレイ領域マネージャー (スクリプト)** コンポーネント。
* 右側に円をクリックして、**セカンダリ マテリアル**プロパティ。
* 検索し、選択、**オクルー ジョン**マテリアルと、ウィンドウを閉じます。

次に、ここ、地球に特別な動作を追加する (sun) などの別のホログラムまたは空間マッピング メッシュ、オクルー ジョンなるたびに青い枠があるようにします。
* **プロジェクト** パネルで、**ホログラム**フォルダー、展開、 **SolarSystem**オブジェクト。
* をクリックして**地球**します。
* **インスペクター**パネルで、地球の資料 (下部にあるコンポーネント)。
* **シェーダー ドロップダウン**、シェーダーを変更**カスタム > OcclusionRim**します。 地球の周りの青の強調表示は、別のオブジェクトによってオクルー ジョンはそのたびにこのレンダリングされます。

最後に、ここ、太陽系惑星の x 線画像視覚効果を有効にします。 編集する必要があります。 **PlanetOcclusion.cs** (Scripts\SolarSystem フォルダーにある)、次を実現するには。
1. 惑星が SpatialMapping レイヤー (ルーム メッシュと平面) によってオクルー ジョンかどうかを決定します。
2. SpatialMapping レイヤーによってオクルー ジョンはそのたびに、惑星のワイヤー フレームの表現を表示します。
3. SpatialMapping 層によってブロックされていない場合は、惑星のワイヤー フレームの表現を非表示にします。

PlanetOcclusion.cs でコーディングの練習に従うか、次のソリューションを使用します。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

**構築し、デプロイ**
* ビルドし、通常どおり、HoloLens をアプリケーションに展開します。
* スキャンが完了する空間のマッピング データの処理を待機 (壁に表示される青い線が表示されます)。
* 太陽系の投影のボックスをオンにし、壁の横にある、またはカウンターの背後にあるボックスを設定します。
* 基本の重なりは、ポスターまたはプロジェクションのボックスにピアリングするサーフェスの背後にある非表示を表示できます。
* 地球を探して、別のホログラムまたは画面に移動するたびに、青の強調表示効果にする必要があります。
* 壁または部屋に他の面の背後にある惑星の移動を観察します。 X 線画像ビジョンなり、ワイヤー フレームのスケルトンを確認できます。

## <a name="the-end"></a>最後です

これで終了です。 完了したので**MR 空間 230。空間マッピング**します。
* Unity 環境と負荷の空間のマッピング、データをスキャンする方法を理解します。
* シェーダーとマテリアルを使用して、再世界を視覚化する方法の基本を理解します。
* 平面を検索およびメッシュから三角形を削除するための新しい処理手法の学習しました。
* 移動し、理にかなっているサーフェイスにホログラムを配置できました。
* 異なるオクルー ジョン手法が発生し、x 線画像のビジョンの電源が利用されています!
