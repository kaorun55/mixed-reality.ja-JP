# <a name="speech-sdk-learning-module"></a>Speech SDK の機械学習モジュール

このチュートリアルでは、Azure Cognitive Services の音声 SDK HoloLens 2 の使用について説明する複合現実のアプリケーションを作成します。 このチュートリアル シリーズを完了したらは、デバイスのマイクを使用して、議事録の作成をリアルタイムでのテキストに音声、音声を他の言語に翻訳および Speech SDK のインテントの機能を使用して音声コマンドを理解するを活用するができます。人工知能します。

目標:

- HoloLens 2 アプリケーションに Azure の Speech SDK を統合する方法について説明します
- 音声コマンドを使用する方法について説明します
- 音声からテキストへの機能を使用する方法について説明します

## <a name="instructions"></a>手順

### <a name="getting-started"></a>作業の開始

1. Unity を起動し、新しいプロジェクトを作成します。 プロジェクト名「Speech SDK ラーニング モジュール」を入力します。 プロジェクトの保存先の場所を選択します。 "プロジェクトの作成。"をクリックします。

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> 注:上記の図のようにテンプレートが"3 D"に設定されていることを確認します。

2. ダウンロード、 [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity パッケージ化し、PC 上のフォルダーに保存します。 Unity プロジェクトにパッケージをインポートします。 これを行う方法の詳細についてを参照してください[ベース モジュール レッスン 1](mrlearning-base-ch1.md)します。 

3. ダウンロードして、Azure のインポート[Speech SDK](https://aka.ms/csspeech/unitypackage) for Unity asset パッケージ。 アセット、"選択「パッケージのインポート、」「カスタムのパッケージ」を選択しをクリックして、Speech SDK パッケージをインポートします。 以前にダウンロードした Speech SDK パッケージを検索してインポート プロセスを開始することを開きます。 

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. 次のポップアップ ウィンドウで、Speech SDK パッケージのインポートを開始するには、[インポート] をクリックします。 次の図に示すように、すべての項目が確認を確認します。

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)


5. ダウンロード、 [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage)資産パッケージ。 Lunarcom アセット パッケージは、資産と Azure の Speech SDK の実際の使用を紹介するこのレッスンのシリーズで開発したスクリプトのコレクションです。 開発された旧暦モジュール アセンブリのエクスペリエンスとのインターフェイスが最終的に音声コマンド ターミナルは、[ベース モジュールのチュートリアル。](mrlearning-base-ch6.md)
6. Mixed Reality Toolkit および Speech SDK をインポートする際と同様の手順に従って、Unity プロジェクトに Lunarcom アセット パッケージをインポートします。
7. Mixed Reality ツールキット (MRTK) を構成します。 この場合、ウィンドウの上部にある"Mixed Reality Toolkit"パネルをクリックし、「シーンと構成に追加します」を選択し、

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

8. シーンようになりましたがいくつかの新しい項目が、MRTK から。 "File"をクリックして別の名前でシーンを保存し"として保存、シーン"SpeechScene"という名前をします。 

   > 注:プロジェクトに、MRTK を追加すると、「再生」モードを入力しないシーンの再生 ボタンを押した場合は、Unity を再起動する必要があります。 

9. "MixedRealityToolkit"オブジェクトを階層内の選択、インスペクターのパネルで「コピーし、カスタマイズ」をクリックします。

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. (の階層で選択されている"MixedRealityToolkit"オブジェクト) と [inspector] パネルで、「有効にする診断システム」の右側にボックスをオフにして、診断システムを無効にします。

![Module4Chapter1step10im](images/module4chapter1step10im.PNG)

11. プロジェクト パネルで、"Lunarcom"フォルダーを展開し、階層に"Lunarcom_Base"プレハブをドラッグします。

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

12. 階層内の"Lunarcom_Base"オブジェクトを選択し、位置が x に設定されていることを確認 = 0、y = 0、および z = 0、x に設定する回転と = 0、y = 0、および z = 0。 読み取りスケールを設定する x = 0.008、y = 0.008、および z 0.01 を =。

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

13. "コンポーネントの追加 をクリックし、検索し、"LunarcomController"を選択します このスクリプトは、手順 6. でインポートした Lunarcom 資産パックに含まれます。

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

14. アプリを Azure Cognitive Services に接続するには、必要がありますキーを入力する"サブスクリプション"とも呼ばれます「API キー」の音声サービス。 手順に従って[このリンク](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started)無料のサブスクリプション キーを取得します。 サブスクリプション キーを取得した後は、次の図に示すように、[inspector] パネルで"LunarcomController"のコンポーネントの「音声認識サービス API キー」フィールドに入力します。

15. インスペクター ウィンドウで"LunarcomController"コンポーネントの「音声サービス地域」フィールドにサブスクリプション キーのサインアップ時に選択したリージョンを入力します。

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

16. 階層内にはの左側にある矢印をクリックして"Lunarcom_Base"オブジェクトを展開し、「ターミナル」次の図に示すように、その子オブジェクトの同じ操作を行います。

17. "Lunarcom_Base"を選択したら、クリックし、テキストをドラッグ"Lunarcom"階層から「出力テキスト」スロットに"LunarcomController"コンポーネントで、[inspector] パネルで次の図に示すようにします。
18. 「ターミナル」スロットに「接続機コント ローラー」スロットに"接続 Light"オブジェクト「ターミナル」のオブジェクトと同じことを行うようになりました。

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

19. Inspector パネル内の"LunarcomController"スクリプトの「Lunarcom ボタン」セクションの横の矢印をクリックして、3 にサイズを変更し、キーボードの Enter または戻り値のキーを押します。 これにより新しい 3 つの"Element"フィールドに表示されます。

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

20. 階層内の横の矢印をクリックして「Lunarcom ボタン」を展開し、上記と同じプロセスを使用して"LunarcomController"のコンポーネントでそれぞれ 0、1、および 2 の要素の参照に Mic、サテライト、およびロケット gameobject にドラッグしますinspector パネル。 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

21. 階層内の"Lunarcom_Base"オブジェクトを選択します。 インスペクター ウィンドウで"コンポーネントの追加 をクリックして、検索し、"LunarcomWakeWordRecognizer。"を選択します。

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

22. "Wake Word"スロットで「ターミナルをアクティブ化します。」に入力します。 また、"Word を閉じます"スロットでは、「Dismiss ターミナル」で入力します。

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="congratulations"></a>結論

音声認識は、Azure を利用した、アプリケーションでセットアップしました。 すべての関数が正常に動作することを確認するアプリケーションを実行します。 手順 22,「ターミナルをアクティブ化します」で型指定されたウェイクという単語を示すと開始します。 次に、音声認識を起動し、読み上げを開始するには、あるマイク ボタンを選択します。 話すと、ターミナルで書き起こし、単語が表示されます。 音声認識を停止する [マイク] ボタンをもう一度キーを押します。 Lunarcom ターミナルを非表示にするには「ターミナル無視」とします。 次のレッスンでは、デバイスを利用した音声認識を使用して、Azure の speech SDK がオフラインになった HoloLens 2 のために使用されていない場合に動的に切り替える方法説明します。

[次のレッスン:Speech SDK レッスン 2](mrlearning-speechSDK-ch2.md)

