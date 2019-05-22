---
title: MR 入力 210 - 視線入力
description: このコーディングの視線の先の概念の詳細については、Unity、Visual Studio および HoloLens の使用に関するチュートリアルに従います。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit unity academy、チュートリアル、視線入力
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993552"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

# <a name="mr-input-210-gaze"></a>MR 入力 210:視線入力

[視線](gaze.md)入力の最初のフォームであり、ユーザーの意図と認識が表示されます。 MR 入力 210 (プロジェクト エクスプ ローラーとも呼ばれます) は、Windows Mixed Reality の視線の先に関連する概念に詳しく知るです。 追加される予定コンテキストの認識をカーソルやホログラム、ユーザーの視線入力について知っている、アプリをフル活用します。

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

ここにあるわかりやすい「宇宙飛行士視線の先の概念を学習するためです。 [MR 基本 101](holograms-101.md)、単純カーソルだけ、視線の先に従う必要があります。 今すぐ歩単純カーソルを移動するとき。

* 行ったカーソルと、ホログラム視線の先に注意してください: - ユーザーが検索している、またはユーザーのいるに基づいてどちらも変更されます*いない*検索します。 これにより、コンテキストに対応しています。
* フィードバックは、カーソルと何が対象の詳細なコンテキストを付与するためにホログラムを追加します。 このフィードバックは、音声と視覚的に指定できます。
* 小規模なターゲットにユーザーを対象とする手法を紹介します。
* 方向インジケーターで、ホログラムにユーザーの注目を集める方法について説明します。
* 彼女は、世界中の周りが移動すると、ユーザーと、ホログラムを実行するための手法を学ぶ。

>[!IMPORTANT]
>以前のバージョンの Unity と Mixed Reality Toolkit を使用して、以下の各章に埋め込まれたビデオが記録されています。 詳細な手順については、正確かつ最新ですが、スクリプトとは、無効な対応するビデオの中でビジュアルを表示があります。 ビデオでは、後生のために含まれる保持され、概念説明のため、引き続き適用されます。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 入力 210:視線入力</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始前の作業

### <a name="prerequisites"></a>前提条件

* 正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。
* 基本的なC#プログラミング機能。
* 完了する必要があります[MR 基本 101](holograms-101.md)します。
* HoloLens デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。

### <a name="project-files"></a>プロジェクト ファイル

* ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip)プロジェクトに必要です。 Unity 2017.2 またはそれ以降が必要です。
* 解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。

>[!NOTE]
>をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)します。

### <a name="errata-and-notes"></a>正誤表と注意事項

* 「マイ コードのみ」を Visual Studio では、する必要がある無効 (オフ) ツール オプション-> コードにブレークポイントをヒットするにはデバッグ-> です。

## <a name="chapter-1---unity-setup"></a>第 1 章 - Unity のセットアップ

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>目標

* HoloLens の開発のためには、Unity を最適化します。
* アセットをインポートして、シーンをセットアップします。
* HoloLens、飛行士を表示します。

### <a name="instructions"></a>手順

1. Unity を起動します。
2. 選択**新しいプロジェクト**します。
3. プロジェクトに名前を**ModelExplorer**します。
4. として場所を入力、**視線**フォルダー アーカイブされた以前のことです。
5. 必ず、プロジェクトに設定されて**3D**します。
6. クリックして**プロジェクトを作成する**します。

### <a name="unity-settings-for-hololens"></a>HoloLens の unity の設定

Unity をエクスポートしようとしましたが、アプリが作成することを把握できるようにする必要があります、[没入型ビュー](app-views.md) 2D ビューではなく。 そのために、HoloLens を仮想現実デバイスとして追加します。

1. 移動して**編集 > プロジェクトの設定 > Player**します。
2. **インスペクター パネル**Player の設定の選択、 **Windows ストア**アイコン。
3. 展開、 **XR 設定**グループ。
4. **レンダリング** セクションで、チェック、**仮想現実サポート**新しいを追加するチェック ボックスをオン**仮想現実 Sdk**一覧。
5. いることを確認**Windows Mixed Reality**一覧に表示されます。 そうでない場合は、選択、 **+** 一覧の下部にあるボタンをクリックし、選択**Windows Holographic**します。

次に、.NET に、スクリプトのバックエンドを設定する必要があります。

1. 移動して**編集 > プロジェクトの設定 > Player** (する必要がありますもこれ前の手順から)。
2. **インスペクター パネル**Player の設定の選択、 **Windows ストア**アイコン。
3. **その他の設定**構成セクションで、必ず**Scripting バックエンド**に設定されている **.NET**

最後に、HoloLens の高速なパフォーマンスを実現するために、品質設定を更新します。

1. 移動して**編集 > プロジェクトの設定 > 品質**します。
2. 下向きの矢印をクリックして、**既定**Windows ストア アイコンの下の行。
3. 選択**非常に低い**の**Windows ストア アプリ**します。

### <a name="import-project-assets"></a>プロジェクトのアセットをインポートします。

1. 右クリックして、**資産**フォルダーで、**プロジェクト**パネル。
2. をクリックして**パッケージ インポート > カスタム パッケージ**します。
3. ダウンロードしたプロジェクト ファイルに移動し、をクリックして**ModelExplorer.unitypackage**します。
4. **[開く]** をクリックします。
5. パッケージが読み込まれると後でをクリックして、**インポート**ボタンをクリックします。

### <a name="setup-the-scene"></a>シーンのセットアップ

1. 階層では、削除、 **Main Camera**します。
2. **HoloToolkit**フォルダーを開き、**入力**フォルダーを開き、**プレハブ**フォルダー。
3. ドラッグ アンド ドロップ、 **MixedRealityCameraParent**からプレハブ、**プレハブ**フォルダーに、**階層**します。
4. 右クリックし、**指向性光**階層し、**削除**します。
5. **ホログラム**フォルダーにドラッグ アンド ドロップは次のアセットのルート、**階層**:
    * **AstroMan**
    * **ライト**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. 開始**再生モード**▶、飛行士を表示します。
7. クリックして**再生モード**をもう一度 ▶**停止**します。
8. **ホログラム**フォルダー、検索、 **Fitbox**資産のルートにドラッグし、**階層**します。
9. 選択、 **Fitbox**で、**階層**パネル。
10. ドラッグ、 **AstroMan**コレクションから、**階層**を**ホログラム コレクション**で Fitbox のプロパティ、**インスペクター**パネル。

### <a name="save-the-project"></a>プロジェクトを保存します

1. 新しいシーンを保存します。**ファイル > としてシーンを保存**します。
2. クリックして**新しいフォルダー**フォルダーの名前と**シーン**します。
3. ファイルに名前を"**ModelExplorer**"で保存し、**シーン**フォルダー。

### <a name="build-the-project"></a>プロジェクトをビルドします

1. Unity では、次のように選択します。**ファイル > Build Settings**します。
2. をクリックして**開くシーンを追加**シーンを追加します。
3. 選択**ユニバーサル Windows プラットフォーム**で、**プラットフォーム**を一覧表示し、クリックして**スイッチ プラットフォーム**します。
4. 具体的には、HoloLens の開発中、設定**ターゲット デバイス**に**HoloLens**します。 それ以外の場合、残して**任意のデバイス**します。
5. 確認**ビルド タイプ**に設定されている**D3D**と**SDK**に設定されている**インストールされている最新**(16299 またはそれ以降の SDK がある必要があります)。
6. **[Build]** をクリックします。
7. 作成、**新しいフォルダー** "App"という名前です。
8. 1 回のクリック、**アプリ**フォルダー。
9. キーを押して**フォルダーを選択します**します。

Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。

1. 開く、**アプリ**フォルダー。
2. 開く、 **ModelExplorer Visual Studio ソリューション**します。

HoloLens へのデプロイ: 場合

1. デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x86**します。
2. ローカル コンピューター] ボタンの横の矢印のドロップダウンをクリックし、[**リモート マシン**します。
3. 入力**HoloLens デバイスの IP アドレス**認証モードを設定および**ユニバーサル (暗号化されていないプロトコル)** します。 クリックして**選択**します。 デバイスの IP アドレスがわからない場合に参照**設定 > ネットワークとインターネット > 詳細オプション**します。
4. 上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。 最初に、デバイスに展開するには、する必要があります[Visual Studio をペアリング](using-visual-studio.md#pairing-your-device-hololens)します。
5. アプリが展開されると、消去、 **Fitbox**で、**ジェスチャ を選択**します。

場合は、イマーシブ ヘッドセットへのデプロイ。

1. デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x64**します。
2. 必ず、配置ターゲットに設定されて**ローカル マシン**します。
3. 上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。
4. アプリが展開されると、消去、 **Fitbox**アニメーション コント ローラーで、トリガーを取得することによって。

## <a name="chapter-2---cursor-and-target-feedback"></a>第 2 章 – カーソルとターゲットのフィードバック

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>目標

* カーソルのビジュアル デ ザインと動作します。
* 視線入力ベースのカーソル フィードバック。
* 視線の先に基づくホログラム フィードバック。

つまり、何らかのカーソルの設計の原則に作業を基にいきます。

* カーソルは、常に存在します。
* カーソルが小さすぎるかビッグを取得することはありません。
* コンテンツの障害を回避します。

### <a name="instructions"></a>手順

1. **HoloToolkit\Input\Prefabs**フォルダー、検索、 **InputManager**資産。
2. ドラッグ アンド ドロップ、 **InputManager**上に、**階層**します。
3. **HoloToolkit\Input\Prefabs**フォルダー、検索、**カーソル**資産。
4. ドラッグ アンド ドロップ、**カーソル**上に、**階層**します。
5. 選択、 **InputManager**オブジェクト、**階層**します。
6. ドラッグ、**カーソル**オブジェクトから、**階層**InputManager に**SimpleSinglePointerSelector**の**カーソル**フィールドで、下部にある、**インスペクター**します。

![簡単な 1 つのポインターのセレクターのセットアップ](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>構築し、デプロイ

1. アプリをリビルド**ファイル > のビルド設定**します。
2. 開く、**アプリ フォルダー**します。
3. 開く、 **ModelExplorer Visual Studio ソリューション**します。
4. クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。
5. カーソルを描画する方法、およびホログラムに触れている場合に外観を変更にする方法を確認します。

### <a name="instructions"></a>手順

1. **階層**パネルで、展開、 **AstroMan**->**GEO_G**->**Back_Center**オブジェクト。
2. ダブルクリックします。 **Interactible.cs** Visual Studio で開きます。
3. 関数が呼び出される、 **IFocusable.OnFocusEnter()** と**IFocusable.OnFocusExit()** コールバック**Interactible.cs**します。 これらはフォーカス (か注視コント ローラーをポイント) を入力し、特定の GameObject のコライダーが終了したときに、Mixed Reality ツールキットの InputManager によって呼び出されます。

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>使用して`EnableKeyword`と`DisableKeyword`上。 作成するには、Toolkit の標準的なシェーダーをアプリにこれらを使用して、従う必要があります、[スクリプトを介したマテリアルにアクセスするための Unity ガイドライン](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)。 この場合は、既に含まれています、[強調表示されているマテリアルの 3 つのバリエーション](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials)リソース フォルダー (の名前で強調表示された 3 つの資料を参照) が必要です。

### <a name="build-and-deploy"></a>構築し、デプロイ

1. 同様に、プロジェクトをビルドし、HoloLens を展開します。
2. オブジェクト、視線の先を目的としたときの動作を確認し、ない場合。

## <a name="chapter-3---targeting-techniques"></a>第 3 章の手法を対象とします。

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>目標

* ターゲット ホログラムを容易にします。
* 頭の自然な動きを安定化します。

### <a name="instructions"></a>手順

1. **階層**パネルで、 **InputManager**オブジェクト。
2. **インスペクター**パネルで、検索、**視線の安定板**スクリプト。 確認する場合 をクリックして Visual Studio で開きます。
    * このスクリプトでは、Raycast データのサンプルを反復処理し、有効桁数が対象とする場合、ユーザーの視線の先を安定化に役立ちます。
3. **インスペクター**、編集することができます、**安定性のサンプルの格納されている**値。 この値は、安定した値を計算する、安定板が反復処理するサンプルの数を表します。

## <a name="chapter-4---directional-indicator"></a>第 4 章 - 方向インジケーター

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>目標

* ホログラムが見つけやすくカーソルに方向インジケーターを追加します。

### <a name="instructions"></a>手順

使用して、 **DirectionIndicator.cs**されるファイル。

1. ユーザーが、ホログラムで gazing しないかどうかに方向インジケーターを表示します。
2. ユーザーが、ホログラムで gazing する場合は、方向インジケーターを非表示にします。
3. ホログラムを指す方向インジケーターを更新します。

それでは始めましょう。

1. をクリックして、 **AstroMan**オブジェクト、**階層**パネルと**矢印をクリックして**を展開します。
2. **階層**パネルで、 **DirectionalIndicator**オブジェクト**AstroMan**します。
3. **インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。
4. メニューで、検索ボックスに入力**方向インジケーター**します。 検索結果を選択します。
5. **階層**パネルにドラッグ アンド ドロップ、**カーソル**オブジェクト、**カーソル**プロパティ、**インスペクター**します。
6. **プロジェクト** パネルで、**ホログラム**フォルダー、ドラッグ アンド ドロップ、 **DirectionalIndicator**上に資産、**方向インジケーター**プロパティ、**インスペクター**します。
7. ビルドして、アプリを展開します。
8. 方向インジケーター オブジェクトは、「宇宙飛行士を検索する方法をご覧ください。

## <a name="chapter-5---billboarding"></a>第 5 章「ビルボード処理

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>目標

* ホログラムが常に手前に直面するには、ビルボード処理を使用します。

使用する、 **Billboard.cs**指向するよう、常に、ユーザーが直面しているが GameObject を保持するファイル。

1. **階層**パネルで、 **AstroMan**オブジェクト。
2. **インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。
3. メニューで、検索ボックスに入力**ビルボード**します。 検索結果を選択します。
4. **インスペクター**設定、**回転軸**に**Y**します。
5. お試しください。 ビルドし、前に、アプリとして展開します。
6. どのビュー ポイントを変更する方法に関係なくのビルボード オブジェクト直面するを参照してください。
7. スクリプトを削除、 **AstroMan**今のところです。

## <a name="chapter-6---tag-along"></a>第 6 章 – Tag-Along

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>目標

* Tag-Along を使用して、室内をフォロー、ホログラムが付いてください。

この問題に取り組んでいます次の設計上の制約によって示されます。

* コンテンツは常にすぐ概要。
* コンテンツは、ようにすることはできません。
* コンテンツの先頭のロックが快適ではありません。

ここで使用するソリューションでは、"tag-along"アプローチを使用します。

Tag-along オブジェクトは、完全には、ユーザーのビューを残します。 考えることができ、ユーザーの頭にラバー バンドでのオブジェクトとしての tag-along にアタッチされています。 ユーザーが移動すると、コンテンツが完全を離れることがなく、ビューの端をスライドして、簡単な概要内で維持されます。 ときに、ユーザーは gazes tag-along オブジェクトの方向より完全に入ったビュー。

使用して、 **SimpleTagalong.cs**されるファイル。

1. Tag-Along オブジェクトがカメラの境界内にあるかどうかを決定します。
2. 指定しない場合、視錐台に視錐台内で部分的に Tag-Along を配置します。
3. それ以外の場合、ユーザーの既定の距離を Tag-Along を配置します。

これを行うには、まず変更、 **Interactible.cs**スクリプトを呼び出す、 **TagalongAction**します。

1. 編集**Interactible.cs**コーディングを完了して 6.a (コメント解除行 84 に 87) を実行します。

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

**InteractibleAction.cs**と組み合わせてスクリプト**Interactible.cs**ホログラムでタップすると、カスタム アクションを実行します。 この場合、tag-along に具体的には 1 つ使用します。

* **スクリプト**フォルダーをクリックします**TagalongAction.cs**資産を Visual Studio で開きます。
* コーディングの練習を行うか、これに変更します。
  * 上部にある、**階層**、検索バーの種類で**ChestButton_Center**結果を選択します。
  * **インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。
  * メニューで、検索ボックスに入力**末尾アクション**します。 検索結果を選択します。
  * **ホログラム**フォルダーの検索、**末尾**資産。
  * 選択、 **ChestButton_Center**オブジェクト、**階層**します。 ドラッグ アンド ドロップ、**末尾**オブジェクトから、**プロジェクト**パネル、**インスペクター**に、**オブジェクトに末尾**プロパティ。
  * ドラッグ、**末尾アクション**オブジェクトから、**インスペクター**に、 **Interactible アクション**フィールドに、 **Interactible**スクリプト。
* ダブルクリックして、 **TagalongAction**スクリプトを Visual Studio で開きます。

![Interactible のセットアップ](images/holograms210-interactible.png)

次を追加する必要があります。

* PerformAction 関数 (InteractibleAction から継承) TagalongAction スクリプトの機能を追加します。
* Gazed 時にオブジェクトをするためのビルボードを追加し、回転軸をお客様 xy のところに設定します。
* 単純な Tag-Along をオブジェクトに追加します。

ここで、ソリューションが**TagalongAction.cs**:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* お試しください。 ビルドして、アプリを展開します。
* コンテンツが、視線入力ポイントの中心を追跡する方法を見ることをブロックすることがなくが、および継続的にします。
