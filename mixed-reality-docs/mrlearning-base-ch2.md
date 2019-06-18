---
title: MR 学習ベース モジュール - ユーザー インターフェイス、手の追跡、Mixed Reality ツールキット構成
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730952"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>MR 学習ベース モジュール - ユーザー インターフェイス、手の追跡、Mixed Reality ツールキット構成

前のレッスンでは、HoloLens 2 の最初のアプリケーションを開始することによって、MRTK によって提供される機能のいくつかを学習しました。 この次のレッスンでは、ボタンと UI テキスト パネルを作成して整理し、既定の操作 (タッチ) を使用して各ボタンを操作する方法を学習します。 また、オブジェクトのサイズ、音、色の変更など、単純なアクションや効果の追加も調査します。 このモジュールでは、空間メッシュの可視化を無効にすることから始めて、MRTK プロファイルを変更する方法に関する基本的な概念を導入します。 

## <a name="objectives"></a>目標

* Mixed Reality ツールキット プロファイルをカスタマイズおよび構成する
* UI 要素とボタンを使用したホログラムの操作
* 基本的な手の追跡の入力と操作

## <a name="instructions"></a>手順

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Mixed Reality ツールキット プロファイルを構成する (空間認識の表示オプションを変更する) 方法
このセクションでは、空間認識メッシュの表示オプションを調整することによって、既定の Mixed Reality ツールキット プロファイルをカスタマイズおよび構成する方法を学習します。 MRTK プロファイル内の設定または値を調整するには、次の同じ原則に従うことができます。

1. [BaseScene] 階層から Mixed Reality ツールキット (MRTK) を選択します。 [インスペクター] パネルで、[Mixed Reality ツールキット スクリプト] を探し、次の図に示すように [アクティブなプロファイル] を選択します。 それをダブルクリックして開きます。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>注:既定では、MRTK プロファイルは編集できません。 これらは既定のプロファイル テンプレートであり、ユーザーは、ここからコピーしてカスタマイズできます。 カスタマイズやプロファイルには複数のレイヤーがあるため、標準的な習慣として、1 つ以上の設定を構成する場合は複数のプロファイルをコピーしてカスタマイズします。
>
>MRTK プロファイルとそのアーキテクチャの詳細については、[MRTK のドキュメント](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)を参照してください。

2. 既定のプロファイルのコピーを作成し、それをカスタマイズします。 既定のプロファイルをコピーするには、[コピーとカスタマイズ] ボタンをクリックします (図を参照)。 これにより、MRTK プロファイルのコピーが作成されます。 MRTK プロファイルの独自のコピーが取得できたので、このプロファイル内の任意の設定をカスタマイズできるようになりました。 以降の手順で説明しているように、このプロファイルの下で入れ子になったすべての追加のプロファイルに対してコピー/カスタマイズ手順を繰り返すことも必要になります。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. 空間認識メッシュの可視性を無効にします。 これを行うには、図に示すように [空間認識システムの設定] を見つけます。 [空間認識システムのプロファイル] の右にある [複製] ボタンをクリックして、既定のプロファイルをカスタマイズ可能なコピーに置き換えます。 下の 2 つ目の図に示すように、ポップアップ ウィンドウが表示された場合は [複製] ボタンを押します。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. 既定の Mixed Reality 空間メッシュ オブザーバーのカスタム コピーを作成します。 [Windows Mixed Reality 空間メッシュ オブザーバー] の横にある下矢印をクリックして追加オプションを表示します。 これらのオプションの中に、灰色表示された (編集できない) [既定の Mixed Reality 空間メッシュ オブザーバー] が表示されます。 この既定のプロファイルをカスタマイズ可能なコピーに置き換えて編集できるようにする必要があります。 右にある (緑色の矢印でマークされた) ボタンをクリックしてコピーを複製します。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. 次に、表示オプションの設定を [オクルージョン] が表示されるように調整します。 これにより、空間メッシュは表示されなくなりますが、引き続きゲーム オブジェクトを空間メッシュの背後に隠します (これはオクルージョンと呼ばれます)。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>注:空間マッピング メッシュは表示されていないときも引き続き存在し、ユーザーから操作できます。 空間マッピング メッシュの背後にホログラムがある場合 (表示された壁の背後にあるホログラムなど)、それらはオクルージョン設定のために表示されません。

これで終了です。 ここまで、MRTK プロファイル内の設定を変更する方法を学習しました。 見てわかるように、MRTK の設定を変更するには、既定のプロファイルのコピーを作成して編集できるようにする必要があります。 新しい設定を含むプロファイルを作成するか、または元の既定のプロファイルを参照する必要が発生した場合は、いつでも (編集できない) 既定のプロファイルに戻ることができます。 調整できる設定には多くのものがあります。 MRTK プロファイルの設定の完全なリファレンスについては、MRTK のドキュメント (https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html ) を参照してください。

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>手の追跡のジェスチャと操作可能なボタン
このセクションでは、手の追跡を使用して操作可能なボタンを押す方法を学習します。

1. プロジェクト フォルダーから [アセット] を選択します。

2. 検索バーに「pressablebutton」と入力します。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. [PressableButton] という名前のプレハブ (青色のボックスで表されています) を階層にドラッグします。 

   > 注:[TMP の基本情報のインポート] に関するメッセージが表示されたら、この時点でそれをインポートしてください。 TMP の基本情報がまだプロジェクトに含まれていない場合は、TMP の基本情報のインポート後にこの手順を繰り返すことが必要になる場合があります。そうしないと、ボタンのテキストが表示されない可能性があります。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. 次の図に示すように、[PressableButton] ゲーム オブジェクト (現在は [BaseScene] 階層内にあります) をダブルクリックしてシーン内に表示します (ボタン画像が次の図とは異なって表示されることがあります)。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. [インスペクター] パネルで、[イベントの追加] をクリックして、押されたら応答するイベントをそのボタンに割り当てます。 表示されるオプションで、ドロップダウン メニューを選択します。 [InteractableOnPressReciever] を選択します。 これにより、このボタンは、追跡対象の手がボタンを押したら押されたイベントに応答できるようになります。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. シーンにキューブを追加します。 階層領域を右クリックして [3D オブジェクト] を選択し、[キューブ] をクリックします ここで、キューブが表示されます。 これは非常に大きく表示されるため、座標を調整して ([キューブ] が引き続き階層領域で選択された状態のまま) サイズを小さくします。 スケール値を x = 0.1、y = 0.1、z = 0.1 に設定します。 キューブをシーン内に配置して、押しボタンの近くだが、ボタンと重ならない位置に置くようにしてください。 次の図では、キューブの位置は x = 0、y = 0.2、z = 1 です。 

   > 注:一般に、Unity の 1 ユニットは現実の世界のほぼ 1 m に相当します。 これには、あるオブジェクトがスケーリングされたオブジェクトの子である場合などの例外があります。
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. この手順では、ボタンが押されたら色を変更するようにキューブを設定します。 [BaseScene] メニューで [PressableButton] を選択します。 [インスペクター] パネルで、[イベントの種類の選択] ボックスの [+] ボタンをクリックします。 次の図に示すように、[BaseScene] メニューの [キューブ] を [ランタイムのみ] ボックスにドラッグします。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

[関数なし] が表示されたドロップダウン リストをクリックします。 [MeshRenderer]、[素材 素材] の順に選択します。 これにより、ボタンが押されたら素材を変更できます。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

プロジェクト パネルに移動し、変更後の素材を検索します。 この例では、素材 [MRTK_Standard_Cyan] を使用します。これを見つけるには、プロジェクト タブの検索バーに「シアン」と入力します (MRTK には、選択できる素材や色が多数が含まれています)。素材を [MeshRenderer.material] の下のボックスにドラッグします。 MRTK の素材は、[アセット]>[MixedRealityToolkit.SDK]>[StandardAssets]>[素材] で見つけることができます。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

これで、このイベントは、ボタンが押されたら、指定された素材に基づいてキューブが色を変更するように設定されました。 この例では、キューブはシアン色に変更されます。

8. 次に、ボタンが放されたら、ボタンが既定の色に戻るように、ボタンを放すアクションを設定します。 手順 7 (前の手順) を繰り返しますが、次の図に示すように、今度は [OnPress] イベントの代わりに [OnRelease] イベントを使用します。

9.  プロジェクト パネルで、ボタンが放されたら既定に戻るキューブの素材を検索します (この場合は、[MRTK_Standard_LightGray] を選択しました)。素材を [MeshRenderer.material] フィールドの下のボックスにドラッグします。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

これで、ボタンが押されたら、新しい色 (シアンなど) に変更され、ボタンが放されたら、指定された元の既定の色 (薄い灰色など) に変更されます。画面の一番上にある [再生] ボタンを押してエディターでそれを試すか、または HoloLens 2 にデプロイしてテストしてください。 エディター内でのシミュレーション (手のシミュレーションを含む) の詳細については、[MRTK のシミュレーションのドキュメント](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)に関するページを参照してください。 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>MRTK のグリッド オブジェクト コレクションを使用したボタンのパネルの作成

このセクションでは、MRTK の GridObjectCollection ツールを使用して、複数のボタンを適切なユーザー インターフェイスに自動的に整合させる方法を学習します。

1. 前のセクションのボタンをボタンが 5 つになるまで複製します。 これを行うには、いくつかの方法があります。
- ボタンを右クリックして [コピー] をクリックした後、ボタンの下に移動し、再度右クリックして [貼り付け] をクリックします。 
- ボタンを右クリックして [複製] をクリックします。 
- キューブをクリックしてキーボード コマンドを使用し、キーボードで [Ctrl D] を押します。

これをボタンが合計 5 つになるまで繰り返します (次の図の 5 つの赤い矢印を参照)。

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. ボタンを空の親ゲーム オブジェクトの下にグループ化します。 ボタンをグリッド コレクションに含めるには、それらのボタンを共通の親オブジェクトの下にグループ化する必要があります。 階層内を右クリックして [空の作成] をクリックします。 これにより、すべてのボタンを配置するための新しい空のゲーム オブジェクトが作成されます。 これは [gameObject] として表示されます。 右クリックし、その名前を [ButtonCollection] に変更します。

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. すべてのボタンを新しいコレクションに移動します。 これを行うには、次の図に示すように、階層内の 5 つのすべてのボタン オブジェクトを選択し、それらをすべて [ButtonCollection] ゲーム オブジェクトの下にドラッグします。 ヒント: 複数の項目を選択するには、項目の選択中に Ctrl キーを押したままにします。

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. MRTK の [グリッド オブジェクト コレクション] コンポーネントをボタン コレクションに追加します。  これを行うには、[ButtonCollection] 親オブジェクトを選択し、[インスペクター] パネルの [コンポーネントの追加] ボタンをクリックします。 次に、検索バーで [グリッド オブジェクト コレクション] を検索し、一覧に表示されたらそれを選択します。

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

[グリッド オブジェクト コレクション] コンポーネントを使用すると、ボタンまたは一連のオブジェクトを適切な行、列、またはグリッドに整理できます。 これは、MRTK によって提供される構成要素の 1 つであり、美しいユーザー インターフェイスを迅速かつ簡単に作成するための方法を提供します。

5. グリッド オブジェクト コレクションを構成します。 すべてのボタンを確実にユーザーの方に向けるには、[向きの種類]、[親を前方に向ける] の順に選択します (図に示します)。次に、ボタンの間のスペースを設定するためにセル サイズを変更します。 [セルの幅] と [セルの高さ] は、次の図に示すように 0.12 ユニット× 0.12 ユニットから始めます。 選択されるオブジェクト/ボタン アセットによっては、これらの値の調整が必要になることがあります。 [行] が 1 に設定されていることを確認してください。 次に、[コレクションの更新] をクリックすると、シーンが次の画像のようになります。 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>注:子オブジェクトまたは親オブジェクトの向きによっては、将来のプロジェクトで、向きの設定を異なった方法で調整することが必要になる可能性があります。 また、コレクション内のオブジェクトのサイズによっては、[セルの幅] や [セルの高さ] のフィールドも異なった方法で定義することが必要になる可能性があります。

### <a name="adding-text-into-your-scene"></a>シーンへのテキストの追加

このセクションでは、テキストを Mixed Reality エクスペリエンスに追加したり編集したりする方法を学習します。 まだ行っていない場合は、[ここ](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)にある手順に従って、Unity で TextMeshPro を有効にするようにしてください。

1. [ButtonCollection] 親オブジェクトを選択し、コレクションを右クリックします。 ドロップダウン メニューで [3D オブジェクト] を展開し、[TextMeshPro - テキスト] を選択します。 次の図に示すように、ボタン コレクションの下に TextMeshPro オブジェクトが表示されます。

![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. TextMeshPro コンポーネントの [テキスト] フィールド (次に示すように、[インスペクター] パネルにあります) に、「ボタン コレクションのテキスト」と入力します。 このテキストはシーン内に表示されますが、ボタンの背後に隠されるか、または間違ったサイズになるか、あるいはその両方になります。

![Lesson2 Chapter4 Step2](images/Lesson2_Chapter4_Step2.JPG)

3. 読みやすさのためにテキストのサイズや位置を改善するには、TextMeshPro コンポーネントの [フォント サイズ] フィールドを調整してフォントのサイズを変更します。 また、次の図に示すように、[四角形の変換] の位置やスケールの調整も必要になる場合があります。 マイクロソフトのテキスト構成に使用される値については次の図を参照し、テキスト フィールドのサイズや位置を改善するための開始点としてこれらの値を自由に使用してください。

![Lesson2 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![Lesson2 Chapter4 Step4](images/Lesson2_Chapter4_Step4.JPG)

5. ボタン オブジェクト上のテキスト値を変更するには、いずれかのボタンの横にある矢印をクリックしてそれを展開し、[SeeItSayItLabel] オブジェクトに移動してから [TextMeshPro] に移動します。そこで、前の手順で説明されているようにボタンのテキストを編集できます。

![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>結論
このレッスンでは、MRTK プロファイルの設定 (つまり、空間認識メッシュの可視性) をコピー、カスタマイズ、および構成する方法を学習しました。また、HoloLens 2 で追跡対象の手を使用して、イベントをトリガーするためにボタンを操作する方法も学習しました。 最後に、Unity の Text Mesh Pro (MRTK の [グリッド オブジェクト コレクション] コンポーネント) を使用して単純な UI インターフェイスを作成する方法を学習しました。

[次のレッスン:ダイナミック コンテンツの配置とソルバー](mrlearning-base-ch3.md)

