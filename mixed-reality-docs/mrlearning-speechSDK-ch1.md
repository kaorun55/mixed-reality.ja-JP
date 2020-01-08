---
title: Azure Speech Services チュートリアル-1. 音声認識と議事録の統合と使用
description: このコースでは、mixed reality アプリケーション内で Azure Speech SDK を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, チュートリアル, hololens
ms.openlocfilehash: 05728cf090b2e998e92980816943a2c3bef18dfb
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334297"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. 音声認識と議事録の統合と使用

## <a name="overview"></a>概要

このチュートリアルでは、Azure Cognitive Services Speech SDK と HoloLens 2 の使用方法を紹介する Mixed Reality アプリケーションを作成します。 このチュートリアルシリーズを完了すると、デバイスのマイクを使用して、音声をリアルタイムでテキストにしたり、音声を他の言語に変換したり、音声認識 SDK の目的機能を活用して、人工の音声コマンドを理解したりすることができます。高度.

## <a name="objectives"></a>目標

* Azure Speech SDK を HoloLens 2 アプリケーションに統合する方法について説明します
* 音声コマンドの使用方法について説明します。
* 音声をテキストに変換する機能の使用方法について説明します。

## <a name="prerequisites"></a>必要条件

>[!TIP]
>[概要チュートリアル](mrlearning-base.md)シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。

* 適切な[ツールがインストール](install-the-tools.md)されている WINDOWS 10 PC
* Windows 10 SDK 10.0.18362.0 以降
* 基本的なC#プログラミング機能
* [開発用に構成され](using-visual-studio.md#enabling-developer-mode)た HoloLens 2 デバイス

>[!IMPORTANT]
>このチュートリアルシリーズでは<a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019.1</a>が必要であり、推奨されるバージョンは unity 2019.1.14 です。 これは、前にリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。

## <a name="getting-started"></a>はじめに

1. Unity を起動し、新しいプロジェクトを作成します。 Project name Speech SDK Learning モジュールを入力します。 プロジェクトを保存する場所を選択します。 [プロジェクトの作成] をクリックします。

    ![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

    >[!NOTE]
    >上の図に示すように、テンプレートが3D に設定されていることを確認します。

2. [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) の Unity [ Foundation パッケージ バージョン 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) をダウンロードし、PC 上のフォルダーに保存します。 Unity プロジェクトにパッケージをインポートします。 これを行う方法の詳細については、入門チュートリアルの「レッスン2」を参照してください[。プロジェクトと最初のアプリケーションを初期化して](mrlearning-base-ch1.md)います。

3. Unity 資産パッケージ用の Azure [SPEECH SDK](https://aka.ms/csspeech/unitypackage)をダウンロードしてインポートします。 [アセット] をクリックし、[パッケージのインポート]、[カスタムパッケージ] の順に選択して、Speech SDK パッケージをインポートします。 先ほどダウンロードした Speech SDK パッケージを検索し、それを開いてインポートプロセスを開始します。

    ![mrlearning-speech-ch1-1-step3a](images/mrlearning-speech-ch1-1-step3a.png)

    ![mrlearning-speech-ch1-1-step3b](images/mrlearning-speech-ch1-1-step3b.png)

4. 次のポップアップウィンドウで [インポート] をクリックして、Speech SDK パッケージのインポートを開始します。 次の図に示すように、すべての項目がチェックされていることを確認します。

    ![mrlearning-speech-ch1-1-step4](images/mrlearning-speech-ch1-1-step4.png)

5. [このリンク](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2)をクリックして、"Lunarcom" パッケージとも呼ばれる Speech SDK モジュールアセットパックをダウンロードします。 Lunarcom 資産パッケージは、このレッスンシリーズ用に開発された資産とスクリプトのコレクションであり、Azure の Speech SDK の実際の使用方法を示しています。 これは、入門チュートリアルで開発した太陰暦モジュールのアセンブリエクスペリエンスに最終的にインターフェイスを提供する音声コマンドターミナルです[。レッスン 7.旧暦モジュールサンプルアプリケーションを作成する](mrlearning-base-ch6.md)。

6. Mixed Reality Toolkit と Speech SDK をインポートする場合と同様の手順に従って、Lunarcom 資産パッケージを Unity プロジェクトにインポートします。

7. Mixed Reality Toolkit (MRTK) を構成します。

    これを行うには、ウィンドウの上部にある [Mixed Reality Toolkit] パネルをクリックし、[シーンに追加] と [構成] を選択します。

    ![mrlearning-speech-ch1-1-step7a](images/mrlearning-speech-ch1-1-step7a.png)

    表示されるポップアップで、[DefaultHoloLens2ConfigurationProfile] を選択して、Mixed Reality Toolkit のアクティブなプロファイルにします。

    ![mrlearning-speech-ch1-1-step7b](images/mrlearning-speech-ch1-1-step7b.png)

8. これで、シーンに MRTK から複数の新しい項目が追加されました。 [ファイル]、[名前を付けて保存] の順にクリックし、シーンに SpeechScene という名前を付けて、シーンを別の名前で保存します。

    >[!NOTE]
    >プロジェクトに MRTK を追加した後にシーンで Play を押すと、再生モードにならない場合は、Unity の再起動が必要になることがあります。

9. シーン階層で MixedRealityToolkit オブジェクトを選択した状態で、[インスペクター] パネルの [& のコピー] をクリックして [複製プロファイル] ポップアップを開きます。 [複製プロファイル] ポップアップで、カスタムプロファイルに適切な名前 (たとえば、Custom HoloLens2ConfigurationProfile) を入力します。 [複製] をクリックしてカスタム構成プロファイルを作成し、アクティブなプロファイルとして設定します。

    ![mrlearning-speech-ch1-1-step9](images/mrlearning-speech-ch1-1-step9.png)

10. また、[インスペクター] パネル (階層で MixedRealityToolkit オブジェクトが選択された状態) で、[診断システムを有効にする] の右側のチェックボックスをオフにして、診断システムを無効にします。

    ![mrlearning-speech-ch1-1-step10](images/mrlearning-speech-ch1-1-step10.png)

11. このチュートリアルでは、音声認識と議事録に入力音声コマンドを使用します。 音声設定を変更するために、入力プロファイルを複製してみましょう。

    シーン階層で MixedRealityToolkit オブジェクトを選択した状態で、[インスペクター] パネルの [小さい複製] ボタンをクリックして、[複製プロファイル] ポップアップを開きます。 [複製プロファイル] ポップアップで、カスタムプロファイルに適切な名前 (たとえば、Custom HoloLens2InputSystemProfile) を入力し、[複製] をクリックしてカスタム入力システムプロファイルを作成し、アクティブなプロファイルとして設定します。

    ![mrlearning-speech-ch1-1-step11](images/mrlearning-speech-ch1-1-step11.png)

12. 入力プロファイルが複製されたら、Speech セクションを展開し、前の手順と同じプロセスに従って speech コマンドプロファイルを複製します。

    ![mrlearning-speech-ch1-1-step12](images/mrlearning-speech-ch1-1-step12.png)

13. [音声] セクションで、[全般設定] に移動し、[開始動作] を [手動開始] に変更します。

    ![mrlearning-speech-ch1-1-step13](images/mrlearning-speech-ch1-1-step13.png)

14. [プロジェクト] パネルで、[Lunarcom] フォルダーを展開し、Lunarcom_Base prefab をシーン階層にドラッグします。

    ![mrlearning-speech-ch1-1-step14](images/mrlearning-speech-ch1-1-step14.png)

15. 階層内の Lunarcom_Base オブジェクトを選択し、位置が x = 0、y = 0、z = 0 に設定されていること、および x = 0、y = 0、z = 0 に設定された回転を確認します。 Scale を read x = 0.008、y = 0.008、および z = 0.01 に設定します。

    ![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. [コンポーネントの追加] をクリックし、[Lunarcom コントローラー] を検索して選択します。 このスクリプトは、手順 6. でインポートした Lunarcom アセットパックに含まれています。

    ![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. アプリケーションを Azure Cognitive Services に接続するには、Speech サービスのサブスクリプションキー (API キーとも呼ばれます) を入力する必要があります。 無料のサブスクリプションキーを取得するには、[こちら](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)の手順に従ってください。 サブスクリプションキーを取得したら、次の図に示すように、[インスペクター] パネルの [LunarcomController] コンポーネントの [Speech Service API キー] フィールドに入力します。

18. [インスペクター] パネルの [LunarcomController] コンポーネントの [Speech Service Region] フィールドに、サブスクリプションキーにサインアップしたときに選択したリージョンを入力します。 たとえば、"westus" という地域では "米国西部" と入力します。

    ![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. 階層で、左側の矢印をクリックして Lunarcom_Base オブジェクトを展開します。 その後、次の図に示すように、子オブジェクト "ターミナル" に対して同じ操作を行います。

20. Lunarcom_Base を選択した状態で、次の図に示すように、階層の Lunarcom テキストをクリックして、[インスペクター] パネルの [LunarcomController] コンポーネントの出力テキストスロットにドラッグします。

21. ターミナルオブジェクトをターミナルスロットに、接続光オブジェクトを接続ライトコントローラースロットに対して同じ操作を行います。

    ![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. [インスペクター] パネルの LunarcomController スクリプトの [Lunarcom ボタン] セクションの横にある矢印をクリックし、サイズを3に変更します。 Enter キーを押すか、戻ります。 これにより、3つの新しい要素フィールドが表示されます。

    ![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. [Lunarcom] ボタンを展開します。このボタンの横にある矢印をクリックし、上記と同じプロセスを使用して、Mic、衛星、およびロケットの各オブジェクトを、次のように、それぞれの LunarcomController コンポーネントの要素0、1、および2にドラッグします。インスペクターパネル。

    ![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. 階層内の Lunarcom_Base のオブジェクトを選択します。 [インスペクター] パネルの [コンポーネントの追加] をクリックし、[Lunarcom Speech レコグナイザー] を検索して選択します。 同じ手順を繰り返して、Lunarcom Wake Word レコグナイザーを追加します。

    ![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. Wake Word スロットで、「Activate Terminal」と入力します。 [Word のスロットを閉じる] に「ターミナルを閉じる」と入力します。

    ![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="build-your-application-to-your-device"></a>デバイスへのアプリケーションのビルド

1. [ファイル > ビルドの設定] に移動して、[ビルドの設定] ウィンドウを再び開きます。

    ![images/mrlearning-ch1-2-ステップ1](images/mrlearning-speach-ch1-2-step1.jpg)

2. [開いているシーンの追加] ボタンをクリックして、試したいシーンが [ビルド内のシーン] リストに含まれていることを確認します。

3. [プレーヤーの設定] ボタンをクリックし、[発行の設定] にアクセスします。 [機能] で、[インターネット]、[インターネットクライアントサーバー]、[プライベートネットワーククライアントサーバー]、[マイクと空間認識] を有効にします。

4. 同じプレーヤー設定で、XR settings にアクセスして、でサポートされている仮想現実を選択します。

5. [ビルド] ボタンを押して、ビルド プロセスを開始します。

    ![mrlearning-ch1-2-手順5](images/mrlearning-speach-ch1-2-step5.jpg)

6. アプリケーション用の新しいフォルダーを作成して、名前を付けます。 下の図では、アプリケーションを含めるために [App] という名前のフォルダーが作成されています。 [フォルダーの選択] をクリックして、新しく作成したフォルダーへのビルドを開始します。 ビルドが完了したら、Unity の [ビルド設定] ウィンドウを閉じてもかまいません。

    ![mrlearning-ch1-2-手順6](images/mrlearning-speach-ch1-2-step6.jpg)

    >[!NOTE]
    >ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。 "エラー: CS0246 = 型または名前空間名" XX "が見つかりませんでした (using ディレクティブまたはアセンブリ参照が不足していることを確認してください)" というエラーが表示された場合は、 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)のインストールが必要になることがあります。

7. ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。 ".Sln" ソリューションファイルをダブルクリックして、Visual Studio でソリューションファイルを開きます。

    >[!NOTE]
    >新しく作成されたフォルダー (前の手順の名前付け規則に従っている場合は "App" フォルダー) を必ず開いてください。これは、ビルドフォルダー内の .sln ファイルとは異なる、同じ名前の .sln ファイルがそのフォルダー外に存在するためです。 

    ![mrlearning-ch1-2-step7](images/mrlearning-speach-ch1-2-step7.jpg)

    >[!NOTE]
    >Visual Studio で新しいコンポーネントのインストールを求められた場合は、 [[ツールのインストール] ページ](install-the-tools.md)で指定したとおりにすべての前提条件コンポーネントがインストールされていることを確認します。

8. USB ケーブルを使って HoloLens 2 を PC に接続します。 これらのレッスンの手順では、HoloLens 2 デバイスを使ってテストをデプロイすることを前提としていますが、[HoloLens 2 エミュレーター](using-the-hololens-emulator.md)にデプロイすることも、[サイドローディング用のアプリ パッケージ](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)を作成することもできます

9. デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。 HoloLens 2 に初めてデプロイする場合は、Visual Studio により、PIN を使用して HoloLens 2 をペアリングするよう求められる場合があります。 開発者モードを有効にするか、Visual Studio とペアリングする必要がある場合は、[こちらの手順](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)に従ってください。

10. [リリース] 構成と [ARM] アーキテクチャを選択して、HoloLens 2 へのビルド用に Visual Studio を構成します。

    ![mrlearning-ch1-2-step10](images/mrlearning-speach-ch1-2-step10.jpg)

11. 最後の手順は、[デバッグ] > [デバッグなしで開始] を選択して、デバイスにビルドすることです。 [デバッグなしで開始] を選択すると、ビルドが成功した時点でアプリケーションがデバイスですぐに起動しますが、Visual Studio にデバッグ情報は表示されません。 これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。 また、[ビルド] > [ソリューションの配置] を選択することで、アプリケーションを自動的に起動せずにデバイスに配置することもできます。

    ![mrlearning-ch1-2-step11.JPG](images/mrlearning-speach-ch1-2-step11.jpg)

## <a name="congratulations"></a>結論

Azure を使用して、アプリケーションに音声認識を設定しました。 アプリケーションを実行して、すべての関数と機能が正常に動作していることを確認します。 まず、「手順 22. ターミナルをアクティブ化する」で入力したウェイクワードを言います。 マイクボタンをクリックして音声認識を開始します。 読み上げを開始します。 書き起こしという単語がターミナルに表示されます。 音声認識を停止するには、マイクボタンをもう一度押します。 「ターミナルを閉じる」と言うと、Lunarcom ターミナルが非表示になります。 次のレッスンでは、HoloLens 2 がオフラインであるために Azure の speech SDK が利用できない場合に、デバイスを使用した音声認識を使用してに動的に切り替える方法について説明します。

[次のチュートリアル: 2. ローカルの音声からテキストへの変換のオフラインモードの追加](mrlearning-speechSDK-ch2.md)
