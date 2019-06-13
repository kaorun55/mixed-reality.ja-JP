---
title: MR 学習ベース モジュール - 高度な入力
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, チュートリアル, hololens
ms.openlocfilehash: 32141aafd43c5d729919673509c93bb2014edd37
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719891"
---
# <a name="mr-learning-base-module---advanced-input"></a>MR 学習ベース モジュール - 高度な入力

このレッスンでは、音声コマンド、パン ジェスチャ、視線追跡などを含む、HoloLens 2 でのいくつかの高度な入力のオプションについて学習します。 

## <a name="objectives"></a>目標

- 音声コマンドとキーワードを使用してイベントをトリガーする方法を学ぶ
- 追跡された手を使用してテクスチャと 3D オブジェクトをパンする
- HoloLens 2 の視線追跡機能を活用してオブジェクトを選択する

## <a name="instructions"></a>手順

### <a name="enabling-voice-commands"></a>音声コマンドの有効化

このセクションでは、2 つの音声コマンドを実装します。 1 つ目として、「toggle diagnostics」(診断をトグル) と言ってフレーム レート診断パネルをトグルします。 2 つ目として、音声コマンドにより音を再生します。 まずは、音声コマンドの構成に必要な MRTK プロファイルと設定を確認します。 

1. [Base Scene] 階層で、[MixedRealityToolkit] を選択します。 [Inspector] (インスペクター) パネルで、下にスクロールして [Input System Settings] (入力システム設定) を探します。 ダブルクリックして、[Input System Profile] (入力システム プロファイル) を開きます。 [レッスン 1](mrlearning-base-ch1.md) で学習したように、入力システム プロファイルをクローンして編集できるようにします。 

入力システム プロファイルには、多くの設定があります。 音声コマンドの設定は、[Speech Command Settings] (音声認識コマンド設定) にあります。 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. [レッスン 1](mrlearning-base-ch1.md) で学習したように、音声認識コマンド プロファイルをクローンして編集できるようにします。 音声認識コマンド プロファイルをダブルクリックすると、多くの設定が表示されます。 これらの設定の詳細については、[MRTK 音声認識に関するドキュメント](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)を参照してください。 

>注:既定では、一般の動作は [Auto Start] (自動で開始) です。 必要であれば [Manual Start] (手動で開始) に変更できますが、この例では [Auto Start] (自動で開始) のままにします。 MRTK には、いくつかの既定の音声コマンドが含まれています (menu (メニュー)、toggle diagnostics (診断のトグル)、toggle profiler (プロファイラーのトグル) など)。 この例では「toggle diagnostics」(診断をトグル) キーワードを使用して、診断フレームレート カウンターのオンとオフを切り替えます。 また、以下のステップで新しい音声コマンドを追加します。
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. 新しい音声コマンドを追加します。 新しい音声コマンドを追加するには、[+ Add a New Speech Command] (新しい音声認識コマンドを追加) ボタンをクリックします。既存の音声コマンドのリストの下に、新しい行が表示されます。 使用したい音声コマンドを入力します。 この例では、「play music」(音楽を再生) コマンドを使用します。

>ヒント:また、音声認識コマンドのキーコードを設定することもできます。 これにより、キーボードのキーを押すことで音声コマンドをトリガーできるようになります。   

4. 音声コマンドに応答する機能を追加します。 [Base Scene] 階層で、他の入力スクリプトが何も追加されていない任意のオブジェクトを選択します (たとえば、操作ハンドラーがない)。[Inspector] (インスペクター) パネルで、[Add Component] (コンポーネントの追加) をクリックします。 「speech input handler」と入力し、 それを選択します。
   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

既定では 2 つのチェックボックスが表示されます。1 つは [is focus required] (フォーカスが必要) チェックボックスです。 これが意味するのは、音声コマンドをトリガーするためには、視線入力の光線 (目の視線入力、頭の視線入力、コントローラーの視線入力、手の視線入力) によってオブジェクトをポイントしていることが必要であるということです。 このチェックボックスのチェックを外して、ユーザーがオブジェクトを見なくても音声コマンドを使用できるようにします。

5. 音声コマンドに応答する機能を追加します。 そうするには、音声入力ハンドラーの [+] ボタンをクリックして、応答するキーワードを選択します。

   > 注:これらのキーワードは、以前のステップで編集したプロファイルに基づいて事前設定されています。

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. [Keyword] (キーワード) の隣にドロップダウン メニューがあります。 [Toggle Diagnostics] (診断をトグル) を選択します。 こうすると、ユーザーが「toggle diagnostics」(診断をトグル) というフレーズを言うたびに、操作がトリガーされるようになります。 場合によっては、隣にある矢印を押して [Element 0] を拡張する必要があります。

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. フレームレート カウンター診断のオンとオフを切り替えるために、[Diagnostics Demo Control] (診断デモ コントロール) スクリプトを追加します。 そうするには、[Add Component] (コンポーネントの追加) ボタンを押して「diagnostics demo control script」を検索し、メニューから追加します。 このスクリプトは任意のオブジェクトに追加できますが、わかりやすさのため、[Speech Input Handler] (音声入力ハンドラー) と同じオブジェクトに追加します。 

   > 注意: このスクリプトはこれらのモジュールにのみ含まれており、元の MRTK には含まれていません。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. [Speech Input Handler] (音声入力ハンドラー) で新しい応答を追加します。 そうするには、[Response ()] の下にある [+] ボタンをクリックします (上の図では緑の矢印で示されています)。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. [Diagnostics Demo Controls] (診断デモ コントロール) スクリプトを持つオブジェクトを、ステップ 8 で作成した新しい応答にドラッグします。
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. ここで [No Function] (関数なし) ドロップダウン リストを選択し、[DiagnosticDemoControls]、[OnToggleDiagnostics ()] の順に選択します。 この関数は、診断のオンとオフを切り替えます。  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> デバイス向けにビルドする前に、マイクの設定を有効にする必要があります。 そうするには、[File] (ファイル) をクリックして [Build Settings] (ビルド設定) に移動し、そこから [Player Settings] (プレーヤーの設定) に移動して、マイクの機能が設定されていることを確認します。

次に、「octa」オブジェクトを使用して音声コマンドからオーディオ ファイルを再生する機能を追加します。 [レッスン 4](mrlearning-base-ch4.md) で、octa オブジェクトにタッチすることでオーディオ クリップを再生する機能を追加したことを思い出してください。 この同じオーディオ ソースを、ミュージック音声コマンドでも活用します。

11. [Base Scene] 階層で octa オブジェクトを選択します。

12. 別の音声入力ハンドラーを追加します (ステップ 4 と 5 を繰り返します) が、octa オブジェクトに対してそうします。 

13. ステップ 6 のように [Toggle Diagnostics] (診断をトグル) 音声コマンドを追加するのではなく、ここでは次の図に示されているように [Play Music] (音楽を再生) 音声コマンドを追加します。
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. ステップ 8 と 9 と同じように、新しい応答を追加し、応答の空のスロットに octa をドラッグします。

15. [No Function] (関数なし) のドロップダウン メニューを選択し、[AudioSource]、[PlayOneShot (AudioClip)] の順に選択します。

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. オーディオ クリップとして、この例では[レッスン 4](mrlearning-base-ch4.md) と同じオーディオ クリップを使用します。 下の図で示されているように、[プロジェクト] パネルに移動して [MRTK_Gem] オーディオ クリップを検索し、オーディオ ソース スロットにドラッグします。 これで、このアプリケーションは「toggle diagnostics」(診断をトグル) 音声コマンドに応答してフレーム レート カウンター パネルをトグルし、「play music」(音楽を再生) 音声コマンドに応答して MRTK_Gem の曲を再生できるようになりました。
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>パン ジェスチャ 

この章では、パン ジェスチャを使用する方法を学びます。 この機能は、スクロール (指または手を使ってコンテンツをスクロールする) に役立ちます。また、パン ジェスチャを使用してオブジェクトを回転させたり、3D オブジェクトのコレクションを次々と表示させたり、2D UI をスクロールさせたりすることさえできます。 ここでは、パン ジェスチャを使用してテクスチャをラップする方法を学びます。 また、3D オブジェクトのコレクションを移動させる方法も学習します。

1. quad を作成します。 [Base Scene] 階層で右クリックして [3D Object] (3D オブジェクト) を選択し、[Quad] を選択します。

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. quad を適切な位置に配置します。 たとえば、カメラから x = 0、y = 0、z = 1.5 の分だけ離れた場所に設定して、HoloLens 2 からのちょうどよい位置に配置します。

   > 注:quad ブロックが以前のレッスンのいずれかのコンテンツの前にある場合、他のオブジェクトをブロックしない場所に移動します。

3. 素材を quad に適用します。 この素材が、パン ジェスチャでスクロールする素材になります。 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. [Project] (プロジェクト) パネルで、検索ボックスに「pan content」と入力します。 この素材を、シーンの quad にドラッグします。 

> 注:「パン コンテンツ」素材は MRTK には含まれていません。以前のレッスンでインポートしたこのモジュールの資産パッケージに含まれています。 

> 注:パン コンテンツを追加すると、引き伸ばされたように見えることがあります。 これを修正するには、quad のサイズの x、y、z 値を希望する大きさになるまで調整します。

パン ジェスチャを使用するには、オブジェクト上のコライダーが必要です。 場合によっては、quad には既にメッシュ コライダーがあります。 ただし、メッシュ コライダーは極めて薄く、選択するのが容易ではないため理想的ではありません。 メッシュ コライダーをボックス コライダーに置き換えることをお勧めします。

5. ([Inspector] (インスペクター) パネルで) quad の上にあるメッシュ コライダーを右クリックして、[Remove Component] (コンポーネントの削除) をクリックして削除します。 
   ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. [Add Component] (コンポーネントの追加) をクリックして [Box Collider] (ボックス コライダー) を検索して、ボックス コライダーを追加します。 追加される既定のボックス コライダーでも薄すぎるので、[Edit Collider] (コライダーの編集) ボタンをクリックします。 ボタンを押すと、x、y、z の値を使用して、またはシーン エディターの要素を使用してサイズを調整できます。 この例では、ボックス コライダーを quad の少し後ろまで拡張します。 シーン エディターで、ボックス コライダーを後ろから外側にドラッグします (下の図を参照してください)。 これにより、ユーザーは指だけでなく手全体を使用してスクロールできるようになります。 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. 操作ができるようにします。 quad を直接操作できるようにしたいので、[Near Interaction Touchable] (近接操作、タッチ可能) コンポーネントを使用します (これはレッスン 4 で octa から音楽を再生するために使用しました)。 下の図に示されているように、[Add Component] (コンポーネントの追加) をクリックして「near interaction touchable」を検索して選択します。 

8. パン ジェスチャを認識する機能を追加します。 [Add Component] (コンポーネントの追加) をクリックして「hand interaction pan」と入力します。 [Hand Ray] (手の光線) (離れたところからパンできるようになる) と [Index Finger] (人差し指) の選択肢があります。 この例では、[Index Finger] (人差し指) のままにします。 
    ![Lesson5 Chapter2 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. [Hand Interaction Pan (Script)] (手による操作、パン (スクリプト)) の [Lock Horizontal] (水平方向のロック) と [Lock Vertical] (垂直方向のロック) チェックボックスでは、それぞれの動きを固定できます。 [Wrap Texture] (テクスチャのラップ) 設定は、テクスチャ (テクスチャ マッピング) がユーザーのパンの動きを追跡できるようにします。 この例では、このボックスにチェックを入れます。 また、[Velocity Active] (速度アクティブ) にチェックを入れない場合、パン ジェスチャは動作しません。 このボックスにもチェックを入れます。 これで、quad のパンが有効になりました。

   

   次に、3D オブジェクトをパンする方法を学びます。 

10. [Quad] オブジェクトを右クリックして [3D Object] (3D オブジェクト) を選択し、[Cube] をクリックします。 cube を、おおよそ x = 0.1、y = 0.1、z = 0.1 になるように大きさを調整します。 cube を 3 回コピーします ([Cube] を右クリックして [Duplicate] (複製) を押すか、Control キーまたは Command キーと D を押します)。 それらを均等に配置します。 シーンは下の画像のようになるはずです。

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. [Quad] をもう一度選択し、[Hand Interaction Pan (Script)] (手による操作、パン (スクリプト)) で、それぞれの cube に対してパンの動作を設定します。 [Pan Event Receivers] (パン イベントのレシーバー) で、イベントを受け取るオブジェクトの数を指定します。 4 つの cube があるので、「4」と入力して Enter キーを押します。 4 つの空のフィールドが表示されます。


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. それぞれの cube を、空の要素スロットにドラッグします。
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. [Move with Pan] (パンに合わせて移動) スクリプトをすべての cube に追加します。 そうするには、Control キーまたは Command キーを長押ししながら、それぞれのオブジェクトを選択します。 その後、[Inspector] (インスペクター) パネルで [Add Component] (コンポーネントの追加) をクリックし、[Move with Pan] (パンに合わせて移動) を検索します。 スクリプトをクリックすると、各 cube に追加されます。 これで 3D オブジェクトはパン ジェスチャに合わせて動くようになります。 quad 上のメッシュの表示を削除した場合、非表示の quad があるはずで、3D オブジェクトのリストからそこにパンできます。

### <a name="eye-tracking"></a>視線追跡

この章では、デモで視線追跡を有効にする方法を学習します。 目の視線入力によって 3D メニュー項目を見つめると、それがゆっくりと回転するようにします。 また、見つめられた項目が選択されると、楽しい効果がトリガーされるようにします。

1. Mixed Reality ツールキット プロファイルが適切に構成されていることを確認します。 執筆時点で、Mixed Reality ツールキット プロファイルの構成には、視線追跡機能は既定では含まれていません。 視線追跡機能を追加するには、[Mixed Reality ツールキット ドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  )の「Setting up the MRTK profiles required for Eye Tracking (視線追跡に必要な MRTK プロファイルを設定する)」にある指示に従ってください。 上記リンク先のドキュメント内のすべての残りのステップに従って、視線追跡が適切に構成されていることを確認します。それには、GazeProvider (カメラに添付されているコンポーネント) 内の視線追跡を有効にすることと、Unity エディターで視線追跡のシミュレーションを有効にすることが含まれます。 MRTK の将来のバージョンには、視線追跡が既定で追加されるかもしれません。

    上記のリンクでは、以下の点についての簡潔な指示があります。

    - MRTK プロファイルで使用するために、Eye Gaze Data Provider を作成する
    - Gaze Provider で視線追跡を有効にする
    - エディターで視線追跡のシミュレーションを設定する
    - Visual Studio ソリューションの機能を編集して、ビルド済みアプリケーションで視線追跡できるようにする

2. [Eye Tracking Target] (視線追跡ターゲット) コンポーネントをターゲット オブジェクトに追加します。 オブジェクトが目の視線入力イベントに応答できるようにするには、目の視線入力を使用して操作したい各オブジェクトに EyeTrackingTarget コンポーネントを追加する必要があります。 このコンポーネントを、グリッド コレクションの一部である 9 つの 3D オブジェクトそれぞれに追加します。 ヒント: 階層内の複数の項目を選択すれば、EyeTrackingTarget コンポーネントを一括で追加できます。
    ![Lesson5 Chapter3 Step2](images/Lesson5Chapter3Step2.JPG)

3. 次に、EyeTrackingTutorialDemo スクリプトを追加して、興味深い操作ができるようにします。 EyeTrackingTutorialDemo スクリプトはこのチュートリアル シリーズのリポジトリに含まれています。Mixed Reality ツールキットには既定では含まれていません。 グリッド コレクションの各 3D オブジェクトに対して、[Add Component] (コンポーネントの追加) メニューからコンポーネントを検索して EyeTrackingTutorialDemo スクリプトを追加します。
   ![Lesson5 Chapter3 Step3](images/Lesson5Chapter3Step3.JPG)

   4. ターゲットを見つめている間、オブジェクトを回転させます。 見つめている間、3D オブジェクトが回転するように構成します。 そうするには、下の図に示されているように、[Eye Tracking Target] (視線追跡ターゲット) コンポーネントの [While Looking At Target] (対象を見つめている間) セクションに新しいフィールドを挿入します。 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



下の図に示されているように、新しく作成されたフィールドで現在のゲーム オブジェクトを空のフィールドに追加して、[EyeTrackingTutorialDemo] > [RotateTarget()] を選択します。 これで、視線追跡により、3D オブジェクトを見つめると回転するように構成できました。 

5. 選択する (エアタップするか、「select」(選択) と言う) 際に見つめられている「ターゲットをブリップする」機能を追加します。 ステップ 4 と同様、EyeTrackingTutorialDemo > BlipTarget() をトリガーするため、これを EyeTrackingTarget コンポーネントのゲーム オブジェクトの "Select()" フィールドに割り当てます (以下の図を参照)。 これを構成したため、エアタップや「select」音声コマンドなどの選択操作をトリガーすると、ゲーム オブジェクト内で短くブリップするようになります。 
    ![Lesson5 Chapter3 Step5](images/Lesson5Chapter3Step5.JPG)
6. HoloLens 2 向けにビルドする前に、視線追跡機能が適切に構成されていることを確かめます。 執筆時点で、Unity では視線入力 (視線追跡のための) 機能を設定することはできません。 HoloLens 2 で視線追跡を使用するには、この機能を設定する必要があります。 次の Mixed Reality ツールキット ドキュメントにある指示に従って、視線入力機能を有効にしてください。 https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>これで終了です。 
これで基本的な視線追跡機能をアプリケーションに追加することができました。 これらの操作は、視線追跡が持つ可能性のほんの一部にすぎません。 この章でレッスン 5 も終了です。このレッスンでは、音声コマンド、パン ジェスチャ、視線追跡などの高度な入力機能について学習しました。 

[次のレッスン:Lunar Module アセンブリのサンプル エクスペリエンス](mrlearning-base-ch6.md)

