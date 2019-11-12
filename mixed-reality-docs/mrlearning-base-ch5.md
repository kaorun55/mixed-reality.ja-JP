---
title: 入門チュートリアル-6. 詳細な入力オプションの調査
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 5599fe48f62a35d1dc02ce30fb7858fd74e87685
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926533"
---
# <a name="6-exploring-advanced-input-options"></a>6. 詳細な入力オプションを調査する

このチュートリアルでは、音声コマンド、パンジェスチャ、および視線追跡の使用を含む、HoloLens 2 の高度な入力オプションをいくつか紹介します。 

## <a name="objectives"></a>目標

- 音声コマンドとキーワードを使用してイベントをトリガーする
- 追跡したハンドを使用して、追跡したハンドでテクスチャと3D オブジェクトをパンする
- HoloLens 2 の監視機能を活用してオブジェクトを選択する

## <a name="instructions"></a>手順

### <a name="enabling-voice-commands"></a>音声コマンドの有効化

このセクションでは、2つの音声コマンドが実装されています。 まず、[診断の切り替え] を表示することによって、フレームレート診断パネルを切り替える機能が導入されました。 次に、音声コマンドでサウンドを再生する機能について説明します。 まず、音声コマンドの構成を担当する MRTK プロファイルと設定を確認します。

1. [BaseScene] 階層で、[MixedRealityToolkit] を選択します。 次に、[インスペクター] パネルで [入力] を選択し、DefaultMixedRealityInputSystemProfile の左側にある小さい [複製] ボタンをクリックして、[複製プロファイル] ポップアップを開きます。 ポップアップで [複製] をクリックして、新しいプロファイル MixedRealityInputSystemProfile を作成します。

    ![mrlearning-base-ch5-1-step1a](images/mrlearning-base-ch5-1-step1a.png)

    これにより、新しく作成された MixedRealityInputSystemProfile で MixedRealityToolkitConfigurationProfile が自動的に設定されます。

    ![mrlearning-base-ch5-1-step1b](images/mrlearning-base-ch5-1-step1b.png)

2. 入力システムプロファイルには、さまざまな設定があります。 音声コマンドの場合は、[音声] セクションを展開し、前の手順と同じ手順を実行して DefaultMixedRealitySpeechCommandsProfile を複製し、独自の編集可能なコピーに置き換えます。

    ![mrlearning-base-ch5-1-step2](images/mrlearning-base-ch5-1-step2.png)

    Speech コマンドプロファイルでは、さまざまな設定がわかります。 これらの設定の詳細については、 [Mrtk speech のドキュメント](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)を参照してください。

    既定では、一般の動作は [Auto Start] (自動で開始) です。 必要に応じて、これを手動で開始するように変更できます。 ただし、この例では、[自動開始] のままにしておきます。 MRTK には、メニュー、診断の切り替え、プロファイラーの切り替えなど、いくつかの既定の音声コマンドが付属しています。 診断フレームカウントカウンターをオンまたはオフにするために、キーワード "診断の切り替え" を使用します。 また、以下のステップで新しい音声コマンドを追加します。

3. 新しい音声コマンドを追加します。 これを行うには、[+ 新しい音声の追加] コマンドボタンをクリックします。 既存の音声コマンドの一覧の下に新しい行が表示されます。 使用する音声コマンドを入力します。 この例では、"play music" コマンドを使用します。

    ![mrlearning-base-ch5-1-step3](images/mrlearning-base-ch5-1-step3.png)

    >[!NOTE]
    >また、音声認識コマンドのキーコードを設定することもできます。 これにより、音声コマンドを使用して、キーボードキーを押したときにイベントをトリガーできます。

4. 音声コマンドに応答する機能を追加します。 MixedRealityPlayspace game オブジェクトなど、他の入力スクリプトがアタッチされていない BaseScene 階層内のオブジェクトを選択します。 [インスペクター] パネルで [コンポーネントの追加] をクリックし、[音声] を検索して、[音声入力ハンドラー] スクリプトを選択します。

    ![mrlearning-base-ch5-1-step4](images/mrlearning-base-ch5-1-step4.png)

    既定では、2つのチェックボックスが表示されます。 1つは [フォーカスが必要] チェックボックスです。 そのため、光を見つめ、ヘッドを見つめ、コントローラーを見つめ、または手動でオブジェクトをポイントしている限り、音声コマンドがトリガーされます。 ユーザーが音声コマンドを使用するためにオブジェクトを確認する必要がないように、このチェックボックスをオフにします。

5. 音声コマンドに応答する機能を追加します。 これを行うには、音声入力ハンドラーにある [+] ボタンをクリックします。

    ![mrlearning-base-ch5-1-step5](images/mrlearning-base-ch5-1-step5.png)

6. [キーワード] の横に、ドロップダウンメニューが表示されます。 [診断の切り替え] を選択すると、ユーザーが "診断の切り替え" という語句が表示されるたびに、アクションがトリガーされます。 要素0を展開するには、その横にある矢印を押す必要があることに注意してください。

    ![mrlearning-base-ch5-1-step6](images/mrlearning-base-ch5-1-step6.png)

    >[!NOTE]
    >これらのキーワードは、手順 3. で編集したプロファイルに基づいて設定されます。

7. 診断システムの音声制御スクリプトを追加して、フレームレートカウンターの診断のオンとオフを切り替えます。 これを行うには、[コンポーネントの追加] をクリックし、[Diagnostics System Voice Controls script] を検索して、メニューから追加します。 このスクリプトは任意のオブジェクトに追加できますが、わかりやすさのため、[Speech Input Handler] (音声入力ハンドラー) と同じオブジェクトに追加します。

    ![mrlearning-base-ch5-1-step7](images/mrlearning-base-ch5-1-step7.png)

8. 音声入力ハンドラーに新しい応答を追加します。 これを行うには、[+] アイコンをクリックして、応答の一覧に新しい応答を追加します。

    ![mrlearning-base-ch5-1-step8](images/mrlearning-base-ch5-1-step8.png)

9. Diagnostics System Voice Controls スクリプトを含むオブジェクトを、前の手順で作成した新しい応答にドラッグします。

    ![mrlearning-base-ch5-1-step9](images/mrlearning-base-ch5-1-step9.png)

10. 関数のドロップダウンをクリックし ([関数なし] と表示されます)、診断システムの音声コントロールを選択し、診断をオンまたはオフに切り替える ToggleDiagnostics () 関数を選択します。

    ![mrlearning-base-ch5-1-step10](images/mrlearning-base-ch5-1-step10.png)

    >[!IMPORTANT]
    > デバイスにビルドする前に、mic 設定を有効にする必要があります。 これを行うには、[ファイル] をクリックし、[ビルドの設定]、[プレーヤーの設定] の順にクリックし、マイクの機能が設定されていることを確認します

    次に、Octa オブジェクトを使用して音声コマンドからオーディオファイルを再生する機能を追加します。 [レッスン 4](mrlearning-base-ch4.md)から、オーディオクリップを再生して、octa オブジェクトにタッチする機能が追加されたことを思い出してください。 この同じオーディオ ソースを、ミュージック音声コマンドでも活用します。

11. BaseScene 階層内の Octa オブジェクトを選択します。

12. 別の音声入力ハンドラーを追加します (手順4と5を繰り返します)。ただし、octa オブジェクトを使用します。

13. 手順6の [診断の切り替え] コマンドを追加するのではなく、次の図に示すように、[音楽音声の再生] コマンドを追加します。

    ![mrlearning-base-ch5-1-step13](images/mrlearning-base-ch5-1-step13.png)

14. 手順 8. と 9. と同様に、新しい応答を追加し、診断システムの音声制御スクリプトを持つオブジェクトである Octa オブジェクトを空の応答スロットにドラッグします。

15. [関数なし] というドロップダウンメニューを選択します。 次に、[オーディオソース]、[PlayOneShot (AudioClip)] の順に選択します。

    ![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. この例では、[レッスン 4](mrlearning-base-ch4.md)と同じオーディオクリップを使用します。 プロジェクトパネルに移動し、"MRTK_Gem" オーディオクリップを検索して、次の図に示すようにオーディオソーススロットにドラッグします。 これで、アプリケーションは音声コマンド "トグル診断" に応答して、フレームレートカウンターパネルを切り替え、音楽を再生して MRTK_Gem 楽曲を再生します。

    ![Lesson5 Chapter1.txt Step16im](images/Lesson5_chapter1_step16im.PNG)

### <a name="the-pan-gesture"></a>パン ジェスチャ

このセクションでは、パンジェスチャの使用方法について説明します。 これは、指またはハンドを使用してコンテンツをスクロールすることでスクロールする場合に便利です。 また、パンジェスチャを使用して、オブジェクトの回転、3D オブジェクトのコレクションの反復処理、または 2D UI のスクロールを行うこともできます。 <!--TMP You will also learn how to use the pan gesture to warp a texture, and how to move a collection of 3D objects.-->

1. quad を作成します。 BaseScene 階層で、右クリックし、[3D オブジェクト] を選択し、次にクワッドを選択します。

    ![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. 必要に応じて、クワッドの位置を変更します。 この例では、HoloLens 2 から快適に使用できるように、x = 0、y = 0、z = 1.5 をカメラから離れた位置に設定します。

    >[!NOTE]
    >4つのブロックまたは前のレッスンの内容の前にある場合は、他のオブジェクトをブロックしないように注意してください。

3. 素材を quad に適用します。 この資料では、パンジェスチャを使用してスクロールします。

    ![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. [プロジェクト] パネルで、検索ボックスに「コンテンツのパン」と入力します。 その素材をシーンのクワッドにドラッグします。

    >[!NOTE]
    >Pan コンテンツマテリアルは MRTK には含まれていませんが、前のレッスンでインポートしたように、このモジュールの資産パッケージのアセットに含まれています。

    >[!NOTE]
    >パン コンテンツを追加すると、引き伸ばされたように見えることがあります。 これを修正するには、quad のサイズの x、y、z 値を希望する大きさになるまで調整します。

    パン ジェスチャを使用するには、オブジェクト上のコライダーが必要です。 場合によっては、quad には既にメッシュ コライダーがあります。 ただし、メッシュ コライダーは極めて薄く、選択するのが容易ではないため理想的ではありません。 メッシュ コライダーをボックス コライダーに置き換えることをお勧めします。

5. [インスペクター] パネルから、クワッド上のメッシュ collider を右クリックします。 次に、[コンポーネントの削除] をクリックして削除します。

    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. 次に、[コンポーネントの追加] をクリックして box collider を追加し、"box collider" を検索します。 既定で追加された box collider はまだ薄くなっているため、[Collider の編集] ボタンをクリックして編集します。 ボタンを押すと、x、y、z の値を使用して、またはシーン エディターの要素を使用してサイズを調整できます。 この例では、ボックス コライダーを quad の少し後ろまで拡張します。 シーン エディターで、ボックス コライダーを後ろから外側にドラッグします (下の図を参照してください)。 これにより、ユーザーは指を使用するだけでなく、スクロールすることもできます。

    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)

7. 操作ができるようにします。 このモジュールを直接操作する必要があるので、ここではレッスン4で、Octa オブジェクトから音楽を再生するために使用した Near インタラクション Touchable コンポーネントを使用します。 [コンポーネントの追加] をクリックし、次の図に示すように "near インタラクション touchable" を検索して選択します。

    ![mrlearning-base-ch5-2-step7a](images/mrlearning-base-ch5-2-step7a.png)

    境界や中心が BoxCollider のサイズや中心に一致しないという警告が黄色で表示されている場合は、[境界の修正] ボタンまたは [修正センター] ボタンをクリックして、中心と境界の値を更新します。

    ![mrlearning-base-ch5-2-step7b](images/mrlearning-base-ch5-2-step7b.png)

8. パン ジェスチャを認識する機能を追加します。 [コンポーネントの追加] をクリックし、検索フィールドに「手動での相互作用」と入力して、ハンドインタラクションのパンズームスクリプトコンポーネントを追加します。

    ![mrlearning-base-ch5-2-step8a](images/mrlearning-base-ch5-2-step8a.png)

    これにより、パン対応のクワッドが用意されています。

    ご覧のように、ハンド対話のパンズームコンポーネントには、オプションの演習としてさまざまな設定があり、自由に再生することができます。

    ![mrlearning-base-ch5-2-step8b](images/mrlearning-base-ch5-2-step8b.png)

<!--TMP
   Next, we will learn how to pan 3D objects. 

10. Right-click the quad object, select 3D object and click Cube. Scale the cube so that it’s roughly x = 0.1, y = 0.1 and z = 0.1. Copy that cube three times by right-clicking the cube and pressing duplicate, or by pressing control/command D. Space them out evenly. Your scene should look similar to the image below.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)

11. Select the quad again and under the hand interaction pan script, set the pan actions to each of the cubes. Under Pan Event Receivers, we want to specify the number of objects receiving the event. Since there are four cubes, type “4” and press Enter. Four empty fields should appear.

![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)

12. Drag each of the cubes into each of the empty element slots.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Add the Move with Pan script to all of the cubes by pressing and holding control/command and select each object. From the Inspector panel, click Add Component and search for “move with pan.” Click the script and it is added to each cube. Now the 3D objects will move with your pan gesture. If you remove the mesh render on your quad, you should now have an invisible quad where you can pan through a list of 3D objects.
-->

### <a name="eye-tracking"></a>視線追跡

このセクションでは、デモで目の追跡を有効にする方法について説明します。 3D メニュー項目が目の gazed になったときに、その項目をゆっくりと回転させます。 また、見つめられた項目が選択されると、楽しい効果がトリガーされるようにします。

1. MRTK プロファイルが視線追跡用に適切に構成されていることを確認します。 これを行うには、「 [MRTK での目の追跡](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)の概要」の手順に進み、「視線[追跡ステップバイステップの設定](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step)」セクションの手順を確認して、目の追跡が適切に構成されていることを確認します。 ドキュメントの残りの手順をすべて完了します。

    >[!NOTE]
    >「 [Mixed Reality Toolkit の構成](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit)」のレッスンで説明されているように、DefaultHoloLens2InputSystemProfile を使用してカスタム MRTK 構成プロファイルを複製する場合、unity プロジェクトではアイ tracking が既定で有効になりますが、unity エディターの視線追跡シミュレーションを設定し、ビルドの目の追跡を許可するように Visual Studio を構成する必要があります。

    上記のリンクでは、以下の点についての簡潔な指示があります。

    - MRTK プロファイルで使用するために Windows Mixed Reality の視線 Data Provider を作成する
    - カメラに接続されている宝石プロバイダーの目の追跡を有効にする
    - Unity エディターでの目の追跡シミュレーションの設定
    - Visual Studio ソリューションの機能を編集して、ビルド済みアプリケーションで視線追跡できるようにする

2. [Eye Tracking Target] (視線追跡ターゲット) コンポーネントをターゲット オブジェクトに追加します。 オブジェクトが視線イベントに応答できるようにするには、視線を使用して操作する各オブジェクトに EyeTrackingTarget コンポーネントを追加する必要があります。 このコンポーネントを、グリッド コレクションの一部である 9 つの 3D オブジェクトそれぞれに追加します。

    >[!TIP]
    >Shift キーまたは ctrl キーを使用してシーン階層内の複数の項目を選択し、EyeTrackingTarget コンポーネントを一括して追加することができます。

    ![Lesson5 Chapter3 のステップごとのステップ](images/Lesson5Chapter3Step2.JPG)

3. 次に、いくつかの魅力的な対話用に EyeTrackingTutorialDemo スクリプトを追加します。 EyeTrackingTutorialDemo スクリプトは、このチュートリアルシリーズリポジトリの一部として含まれています。 混合 Reality ツールキットには、既定では含まれていません。 Grid コレクション内の3D オブジェクトごとに、[コンポーネントの追加] メニューでコンポーネントを検索して、EyeTrackingTutorialDemo スクリプトを追加します。

   ![Lesson5 Chapter3 手順3](images/Lesson5Chapter3Step3.JPG)

4. ターゲットを見つめている間、オブジェクトを回転させます。 3D オブジェクトを見ながらスピンするように構成したいと考えています。 これを行うには、次の図に示すように、EyeTrackingTarget コンポーネントの Target () セクションを参照しながら、に新しいフィールドを挿入します。

    ![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)

    新しく作成されたフィールドで、次の図に示すように、現在の Game オブジェクトを空のフィールドに追加し、EyeTrackingTutorialDemo > RotateTarget () を選択します。 これで、視線追跡により、3D オブジェクトを見つめると回転するように構成できました。

    ![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)

5. エアタップによって、または "select" と言ったときに、選択時に gazed される "ブリップが発生 target" の機能を追加します。 手順4と同様に、次の図に示すように、EyeTrackingTarget コンポーネントの game オブジェクトの Select () フィールドに割り当てることによって、EyeTrackingTutorialDemo > をトリガーします。 これで構成が完了すると、エアタップや音声コマンドの "select" などの選択アクションをトリガーするたびに、game オブジェクトにわずかなブリップが発生が見られます。

    ![Lesson5 Chapter3 手順5](images/Lesson5Chapter3Step5.JPG)

6. HoloLens 2 向けにビルドする前に、視線追跡機能が適切に構成されていることを確かめます。 このドキュメントの執筆時点では、Unity には、視線追跡機能に対して、宝石入力を設定する機能がまだありません。 この機能の設定は、監視が HoloLens 2 で動作するために必要です。 「 [HoloLens 2 での Unity アプリのテスト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)」の手順に従って、宝石入力機能を有効にします。

## <a name="congratulations"></a>結論

アプリケーションに基本的な監視機能が正常に追加されました。 これらの操作は、視線追跡が持つ可能性のほんの一部にすぎません。 また、レッスン5では、音声コマンド、パンジェスチャ、視線追跡などの高度な入力機能について学習しました。

[次のレッスン: 7. 旧暦モジュールサンプルアプリケーションの作成](mrlearning-base-ch6.md)
