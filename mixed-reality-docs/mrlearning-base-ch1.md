---
title: MR Learning ベースのモジュールのプロジェクトの初期化と最初のアプリケーション
description: このコースでは、複合現実のアプリケーション内で Azure の顔認識機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 複合現実、unity、チュートリアル、hololens
ms.openlocfilehash: c5490e6a3b542a5ca677b309e5ed1171f8666fe7
ms.sourcegitcommit: b5bad4eeb5cdd0c2a7b639442656c306e8b5853b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65814011"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>MR Learning ベースのモジュールのプロジェクトの初期化と最初のアプリケーション

この最初のレッスンでは、提供、HoloLens 2 の最初のアプリケーションを起動し、デバイスにデプロイする Mixed Reality ツールキットには、機能について説明します。

## <a name="objectives"></a>目標

* HoloLens の開発のためには、Unity を最適化します。
* アセットをインポートして、シーンをセットアップします。
* 空間メッシュ、手の形のメッシュとフレーム レート カウンターの視覚化。

## <a name="instructions"></a>手順

### <a name="create-new-unity-project"></a>新しい Unity プロジェクトを作成します。

1. Unity を起動します。
2. **[新規]** を選択します。
![レッスン 1 から第 1 章の手順 2](images/Lesson1Chapter1Step2.JPG)
3. プロジェクト名を入力します (例。"MixedRealityBase")。
![レッスン 1 から第 1 章の手順 3](images/Lesson1Chapter1Step3.JPG)
4. プロジェクトを保存する場所を入力します。
![レッスン 1 から第 1 章の手順 4](images/Lesson1Chapter1Step4.JPG)
5. 必ず、プロジェクトに設定されて**3D**します。
![レッスン 1 から第 1 章の手順 5](images/Lesson1Chapter1Step5.JPG)
6. クリックして**プロジェクトを作成する**します。
![レッスン 1 から第 1 章の手順 6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality 用 Unity プロジェクトを構成します。

1. ファイルにアクセスして、ビルド設定 ウィンドウを開く > ビルドの設定。
![レッスン 1 から第 4 章の手順 1](images/Lesson1Chapter4Step1.JPG)
2. 「ユニバーサル Windows プラットフォーム」を選択して「ユニバーサル Windows プラットフォーム」に切り替えるし、プラットフォームの切り替えを「プラットフォームの切り替え」ボタンをクリックします。 HoloLens 2 で実行されているアプリは、ユニバーサル Windows プラットフォーム (UWP) する必要があります。
![レッスン 1 から第 4 章の手順 2](images/Lesson1Chapter4Step2.JPG)
3. ビルド ウィンドウで、Player の設定 をクリックして仮想現実を有効にし、inspector パネルでチェック ボックスをオン、「仮想現実サポートされて」XR の設定で次の図に示すようにします。 Inspector パネルを表示するには、[ビルド設定] ウィンドウを邪魔をドラッグする必要がありますに注意してください。 「仮想現実サポート」チェック ボックスは、複合現実にも適用されます/AR ヘッドセット ステレオスコ ピック ビジョン (レンダリングごとに異なるイメージ目ごとです) の有効化、を参照しています。![レッスン 1 から第 4 章の手順 3](images/Lesson1Chapter4Step3.JPG)
4. 同じ inspector] パネルで、[機能] セクションで「空間認識」のチェック ボックスが有効である [発行の設定を確認します。 空間認識は、HoloLens 2 などの複合現実デバイスに空間マッピングのメッシュを視覚化できます。 インスペクター ウィンドウ上の「XR 設定」と"その他の設定 の下で発行の設定があります。
![レッスン 1 から第 4 章の手順 4](images/Lesson1Chapter4Step4.JPG)

> 注: 有効にするいくつかその他の一般的な機能が含まれます (音声コマンド) のマイクと InternetClient (ネットワーク接続が必要なサービスに接続する) のこのセクションでは使用されませんが、

### <a name="import-the-mixed-reality-toolkit"></a>インポート、Mixed Reality Toolkit

1. ダウンロード、 [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) unity パッケージ化し、PC 上のフォルダーに保存します。

2. 資産をクリックして、Mixed Reality Toolkit パッケージをインポート > インポート > カスタム パッケージ。 手順 1. でダウンロードした Mixed Reality Toolkit パッケージを検索してインポート プロセスを開始することを開きます。 インポートのプロセスには数分お待ちください。
    ![レッスン 1 から第 2 章 Step2a](images/Lesson1Chapter2Step2a.JPG) ![レッスン 1 から第 2 章 Step2b](images/Lesson1Chapter2Step2b.JPG)

3. [次へ] のポップアップ ウィンドウでは、Mixed Reality Toolkit のインポートを開始するには、[インポート] をクリックします。 図のように、すべての項目が確認を確認します。 Mixed Reality Toolkit の既定の設定を適用するよう求めるポップアップ ダイアログ ボックスを表示する場合は、「適用します」をクリックします
    ![レッスン 1 から第 2 章 Step3](images/Lesson1Chapter2Step3.JPG) ![レッスン 1 から第 2 章の手順 3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Mixed Reality ツールキットを構成します。

1. Mixed Reality Toolkit バー、メニューから選択して、混合 Toolkit の構成 > 構成します。 複合現実ツールキットをインポートした後、このメニュー項目が表示されない場合は、Unity を再起動してください。
![レッスン 1 から第 3 章の手順 1](images/Lesson1Chapter3Step1.JPG)
2. シーンようになりましたがいくつかの新しい項目と変更が Mixed Reality Toolkit から。 ファイルをクリックして別の名前で、シーンを保存 > として保存し、シーン BaseScene などの名前を入力します。 プロジェクトの Assets フォルダーで「シーン」フォルダーに保存して別に整理されたシーンを保持します。
![レッスン 1 から第 3 章 Step2a](images/Lesson1Chapter3Step2a.JPG)
![レッスン 1 から第 3 章 Step2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>デバイスにアプリケーションを構築します。

1. 前のセクションからのビルド設定ウィンドウを閉じた場合、ビルド設定 ウィンドウ再度開くファイルに移動して > ビルドの設定。
    ![レッスン 1 から第 5 章の手順 1](images/Lesson1Chapter5Step1.JPG)

2. 試したいシーンが「開いているシーンを追加」ボタンをクリックして、"Scenes in Build"一覧に確認してください。

3. ビルド プロセスを開始するビルド ボタンを押します。
    ![レッスン 1 から第 5 章の手順 3](images/Lesson1Chapter5Step3.JPG)

4. 作成し、アプリケーションの新しいフォルダーの名前します。 名前のフォルダーの下の図の"App"は、アプリケーションを含むに作成されました。 新しく作成したフォルダーにビルドを開始「フォルダーの選択」をクリックします。 ビルドが完了すると、Unity で [ビルド設定] ウィンドウを閉じると可能性があります。 
    ![レッスン 1 から第 5 章の手順 4](images/Lesson1Chapter5Step4.JPG)

  > 注: 構成をもう一度お試しください、ビルドが失敗した場合、または Unity を再起動して、再構築します。 エラーを表示する場合は、"エラー。CS0246 ="XX"が見つかりませんでした型または名前空間の名前 (が存在することを使用して、ディレクティブまたはアセンブリ参照か。)"、をインストールする必要がありますし、 [Windows 10 SDK (10.0.18362.0)。](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. ビルドが完了した後、新しくビルドされたアプリケーション ファイルを格納している新しく作成したフォルダーを開きます。 "MixedRealityBase.sln"ソリューション (または、プロジェクトの代替名を使用した場合は、対応する名前) をダブルクリックすると、Visual Studio でソリューション ファイルを開きます。

  > 注:(つまり、"App"フォルダーを前の手順から名前付け規則に従う場合)、新しく作成したフォルダーを開くことを確認するように、ビルド フォルダー内の .sln ファイルと混同しないように、そのフォルダーの外部で同様に名前付きの .sln ファイルがあります。 

![レッスン 1 から第 5 章の手順 5](images/Lesson1Chapter5Step5.JPG)

  > 注:Visual Studio、新しいコンポーネントをインストールするよう求めるお聞かせくださいとしてすべての前提条件となるコンポーネントがインストールされていることを確認する場合で指定された["ツールをインストールする ページ](install-the-tools.md)

6. USB ケーブルを使用して PC、HoloLens 2 に差し込みます。 レッスンの手順では、HoloLens 2 デバイスでのテスト、デプロイする前提としています、中にすることもできますを展開する、 [HoloLens 2 エミュレーター](using-the-hololens-emulator.md)を作成することも、[サイドローディング用アプリ パッケージ](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. デバイスに、ビルド前に、デバイスが開発者モードであることを確認します。 初めて HoloLens 2 へのデプロイの場合は、Visual Studio に、pin、HoloLens 2 をペアリングするように指示する可能性があります。 従ってください[手順](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)開発者モードを有効にするか、Visual Studio とペアリングする必要がある場合。

8. "Release"構成と"ARM"アーキテクチャを選択して、HoloLens 2 を構築するための Visual Studio を構成します。
    ![レッスン 1 から第 5 章 Step8](images/Lesson1Chapter5Step8.JPG)

9. 最後に、デバッグを選択して、デバイスにビルド > デバッグなしで開始します。 "デバッグなしで開始 を選択すると、デバイス ビルドに成功すると、Visual Studio に表示されるデバッグ情報なしですぐに開始するアプリケーションとされます。 つまり、アプリケーションのアプリケーションを停止することがなく、HoloLens 2 で実行中に、USB ケーブルを切断することができます。 ビルドを選択することも > を自動的に起動するアプリケーションをしなくても、デバイスに展開するには、ソリューションの配置。
    ![レッスン 1 から第 5 章 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>おめでとうございます

今すぐが配置されました、最初の HoloLens 2 アプリケーション。 周りを説明しながら、HoloLens 2 によって認識されているすべてのサーフェイスをカバーする空間メッシュが表示されます。 さらに、ハンドと本の指を追跡し、アプリのパフォーマンスを監視するためのフレーム レート カウンターにインジケーターを表示する必要があります。 これらは、基礎となる部分、Mixed Reality ツールキットを使用して、すぐに付属のほんの一部です。 付属のレッスンでは、HoloLens 2 や Mixed Reality ツールキットの機能を十分に検証できるように、シーンへのコンテンツや対話機能の追加を開始します。

>注:音声コマンドを使用して、フレーム レート カウンターを切り替える方法を説明する[レッスン 5](mrlearning-base-ch5.md)

[次のレッスン:ユーザー インターフェイス、追跡、および現実ツールキットの構成を混在手の形](mrlearning-base-ch2.md)
