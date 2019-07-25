---
title: MR Learning SpeechSDK モジュール-音声認識と議事録
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: c1ca44ffcaa8dced988b829d9875ebe304f14a12
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460354"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. 音声認識と議事録の統合と使用

このチュートリアルでは、Azure Cognitive Services Speech SDK と HoloLens 2 の使用方法を紹介する Mixed Reality アプリケーションを作成します。 このチュートリアルシリーズを終了すると、デバイスのマイクを使用して、音声をリアルタイムでテキストにしたり、音声を他の言語に翻訳したり、音声認識機能を活用して音声コマンドを理解したりすることができます。人工知能。

## <a name="objectives"></a>目的

- Azure Speech SDK を HoloLens 2 アプリケーションに統合する方法について説明します
- 音声コマンドの使用方法について説明します。
- 音声をテキストに変換する機能の使用方法について説明します。

## <a name="instructions"></a>手順

### <a name="getting-started"></a>作業の開始

1. Unity を起動し、新しいプロジェクトを作成します。 Project name Speech SDK Learning モジュールを入力します。 プロジェクトを保存する場所を選択します。 次に、[プロジェクトの作成] をクリックします。

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> 注:上の図に示すように、テンプレートが3D に設定されていることを確認します。

2. [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity パッケージをダウンロードし、PC 上のフォルダーに保存します。 Unity プロジェクトにパッケージをインポートします。 これを行う方法の詳細については、「[基本モジュールレッスン 1](mrlearning-base-ch1.md)」を参照してください。 

3. Unity 資産パッケージ用の Azure [SPEECH SDK](https://aka.ms/csspeech/unitypackage)をダウンロードしてインポートします。 [アセット] をクリックし、[パッケージのインポート]、[カスタムパッケージ] の順に選択して、Speech SDK パッケージをインポートします。 先ほどダウンロードした Speech SDK パッケージを検索し、それを開いてインポートプロセスを開始します。 

![Module4Chapter1step3ima](images/module4chapter1step3ima.PNG)

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. 次のポップアップウィンドウで [インポート] をクリックして、Speech SDK パッケージのインポートを開始します。 次の図に示すように、すべての項目がオンになっていることを確認します。

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)

5. Speech SDK モジュールアセットパックをダウンロードします。[このリンク](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2)をクリックして、Lunarcom パッケージとしても知られています。 Lunarcom 資産パッケージは、このレッスンシリーズ用に開発された資産とスクリプトのコレクションであり、Azure の Speech SDK の実際の使用方法を示しています。 これは、[基本的なモジュールのチュートリアル](mrlearning-base-ch6.md)で開発した太陰暦モジュールのアセンブリエクスペリエンスと最終的に連携する音声コマンド端末です。

6. Mixed Reality Toolkit と Speech SDK をインポートする場合と同様の手順に従って、Lunarcom 資産パッケージを Unity プロジェクトにインポートします。
7. Mixed Reality Toolkit (MRTK) を構成します。 これを行うには、ウィンドウの上部にある [Mixed Reality Toolkit] パネルをクリックし、[シーンに追加] と [構成] を選択します。

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

![module4Chapter1step9ima](images/module4chapter1step9ima.PNG)

![module4Chapter1step9imb](images/module4chapter1step9imb.PNG)

8. これで、シーンに MRTK から複数の新しい項目が追加されました。 [ファイル]、[名前を付けて保存] の順にクリックし、シーンに SpeechScene という名前を付けて、シーンを別の名前で保存します。 

> 注:プロジェクトに MRTK を追加した後にシーンで Play を押すと、再生モードにならない場合は、Unity の再起動が必要になることがあります。 

9. 階層で MixedRealityToolkit オブジェクトを選択した状態で、[インスペクター] パネルの [コピーとカスタマイズ] をクリックします。

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. また、[インスペクター] パネル (階層で MixedRealityToolkit オブジェクトが選択された状態) で、[診断システムを有効にする] の右側のチェックボックスをオフにして、診断システムを無効にします。

![Module4Chapter1step9imd](images/module4chapter1step9imd.PNG)

11. 音声コマンドを有効にするには、新しく作成した MRTK プロファイルを選択してカスタマイズします。 このチュートリアルでは、音声認識と議事録に入力音声コマンドを使用します。 入力プロファイルを複製して、音声設定を変更できます。

![Module4Chapter1step11imb](images/module4chapter1step11imb.PNG)

![Module4Chapter1step11imd](images/module4chapter1step11imd.PNG)

12. 入力プロファイルが複製されたら、音声コマンドにアクセスして、音声コマンドを複製します。

![Module4Chapter1step12imb](images/module4chapter1step12imb.PNG)

![Module4Chapter1step12imc](images/module4chapter1step12imc.PNG)

13. [音声コマンド] で、[全般設定] にアクセスし、[開始動作] を [手動開始] に設定します。

![Module4Chapter1step13imb](images/module4chapter1step13imb.PNG)

14. [プロジェクト] パネルで、[Lunarcom] フォルダーを展開し、Lunarcom_Base prefab を階層にドラッグします。

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

15. 階層内の Lunarcom_Base オブジェクトを選択し、位置が x = 0、y = 0、z = 0 に設定されていること、および x = 0、y = 0、z = 0 に設定されていることを確認します。 Scale を read x = 0.008、y = 0.008、および z = 0.01 に設定します。

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. [コンポーネントの追加] をクリックし、[LunarcomController] を検索して選択します。 このスクリプトは、手順 6. でインポートした Lunarcom アセットパックに含まれています。

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. アプリケーションを Azure Cognitive Services に接続するには、Speech サービスのサブスクリプションキー (API キーとも呼ばれます) を入力する必要があります。 無料のサブスクリプションキーを取得するには、[こちら](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started)の手順に従ってください。 サブスクリプションキーを取得したら、次の図に示すように、[インスペクター] パネルの [LunarcomController] コンポーネントの [Speech Service API キー] フィールドに入力します。

18. [インスペクター] パネルの [LunarcomController] コンポーネントの [Speech Service Region] フィールドに、サブスクリプションキーにサインアップしたときに選択したリージョンを入力します。 たとえば、"westus" という地域では "West US" という種類を使用します。

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. 階層内で、左側の矢印をクリックして、Lunarcom_Base オブジェクトを展開します。 その後、次の図に示すように、子オブジェクト "ターミナル" に対して同じ操作を行います。

20. Lunarcom_Base を選択した状態で、次の図に示すように、階層の Lunarcom テキストをクリックし、[インスペクター] パネルの [LunarcomController] コンポーネントの出力テキストスロットにドラッグします。

21. ターミナルオブジェクトをターミナルスロットに、接続光オブジェクトを接続ライトコントローラースロットに対して同じ操作を行います。

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. [インスペクター] パネルの LunarcomController スクリプトの [Lunarcom ボタン] セクションの横にある矢印をクリックし、サイズを3に変更します。 Enter キーを押すか、戻ります。 これにより、3つの新しい要素フィールドが表示されます。

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. [Lunarcom] ボタンを展開します。このボタンの横にある矢印をクリックし、上記と同じプロセスを使用して、Mic、衛星、およびロケットの各オブジェクトを、次のように、それぞれの LunarcomController コンポーネントの要素0、1、および2にドラッグします。インスペクターパネル。 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. 階層内の Lunarcom_Base オブジェクトを選択します。 [インスペクター] パネルの [コンポーネントの追加] をクリックし、LunarcomWakeWordRecognizer を検索して選択します。

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. Wake Word スロットで、「Activate Terminal」と入力します。 [Word のスロットを閉じる] に「ターミナルを閉じる」と入力します。

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a>デバイスへのアプリケーションのビルド

1. [ファイル > ビルドの設定] に移動して、[ビルドの設定] ウィンドウを再び開きます。

![レッスン1から Chapter5 手順](images/Lesson1Chapter5Step1.JPG)

2. [開いているシーンの追加] ボタンをクリックして、試したいシーンが [ビルド内のシーン] リストに含まれていることを確認します。

3. [ビルド] ボタンを押して、ビルド プロセスを開始します。

![レッスン1から Chapter5 手順3](images/Lesson1Chapter5Step3.JPG)

4. アプリケーション用の新しいフォルダーを作成して、名前を付けます。 下の図では、アプリケーションを含めるために [App] という名前のフォルダーが作成されています。 [フォルダーの選択] をクリックして、新しく作成したフォルダーへのビルドを開始します。 ビルドが完了したら、Unity の [ビルド設定] ウィンドウを閉じてもかまいません。 

![レッスン1から Chapter5 手順4](images/Lesson1Chapter5Step4.JPG)

> 注: ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。 [エラー:CS0246 = “XX” という名前の型または名前空間が見つかりませんでした (ディレクトリの使用またはアセンブリ参照が不足しています)] のようなエラーが表示される場合は、[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) のインストールが必要な場合があります

5. ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。 ".Sln" ソリューションファイルをダブルクリックして、Visual Studio でソリューションファイルを開きます。

> 注:必ず、新しく作成したフォルダー (つまり、前の手順で名前付け規則に従っている場合は、[App] フォルダー) を開いてください。そのフォルダーの外部に同じような名前の .sln ファイルがあり、ビルド フォルダー内の .sln ファイルと混同してはならないためです。 

![Lesson1 Chapter5 Step5](images/Lesson1Chapter5Step5.JPG)

> 注:Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、[「ツールのインストール」ページ](install-the-tools.md)で示されている、前提条件となるすべてのコンポーネントがインストールされていることを確認してください

6. USB ケーブルを使って HoloLens 2 を PC に接続します。 これらのレッスンの手順では、HoloLens 2 デバイスを使ってテストをデプロイすることを前提としていますが、[HoloLens 2 エミュレーター](using-the-hololens-emulator.md)にデプロイすることも、[サイドローディング用のアプリ パッケージ](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)を作成することもできます

7. デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。 HoloLens 2 に初めてデプロイする場合は、Visual Studio により、PIN を使用して HoloLens 2 をペアリングするよう求められる場合があります。 開発者モードを有効にするか、Visual Studio とペアリングする必要がある場合は、[こちらの手順](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)に従ってください。

8. [リリース] 構成と [ARM] アーキテクチャを選択して、HoloLens 2 へのビルド用に Visual Studio を構成します。

![レッスン1から Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. 最後の手順は、[デバッグ] > [デバッグなしで開始] を選択して、デバイスにビルドすることです。 [デバッグなしで開始] を選択すると、ビルドが成功した時点でアプリケーションがデバイスですぐに起動しますが、Visual Studio にデバッグ情報は表示されません。 これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。 また、[ビルド] > [ソリューションの配置] を選択することで、アプリケーションを自動的に起動せずにデバイスに配置することもできます。

![レッスン1から Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>結論

Azure を使用して、アプリケーションに音声認識を設定しました。 アプリケーションを実行して、すべての関数と機能が正常に動作していることを確認します。 まず、「手順 22. ターミナルをアクティブ化する」で入力したウェイクワードを言います。 マイクボタンをクリックして音声認識を開始します。 読み上げを開始します。 書き起こしという単語がターミナルに表示されます。 音声認識を停止するには、マイクボタンをもう一度押します。 「ターミナルを閉じる」と言うと、Lunarcom ターミナルが非表示になります。 次のレッスンでは、HoloLens 2 がオフラインであるために Azure の speech SDK が利用できない場合に、デバイスを使用した音声認識を使用してに動的に切り替える方法について説明します。

[次のチュートリアル:2. ローカル音声からテキストへの変換用のオフライン モードの追加](mrlearning-speechSDK-ch2.md)

