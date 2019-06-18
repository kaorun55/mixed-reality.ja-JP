---
title: ML 学習ベース モジュール - プロジェクトの初期化と最初のアプリケーション
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: c5490e6a3b542a5ca677b309e5ed1171f8666fe7
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "65814011"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>ML 学習ベース モジュール - プロジェクトの初期化と最初のアプリケーション

この最初のレッスンでは、Mixed Reality ツールキットが提供し、HoloLens 2 用の最初のアプリケーションを起動してデバイスにデプロイする必要のある機能について学習します。

## <a name="objectives"></a>目標

* HoloLens 用 Unity の開発を最適化する。
* アセットをインポートし、シーンをセットアップする。
* 空間のメッシュ、手の形のメッシュ、およびフレームレート カウンターの視覚化。

## <a name="instructions"></a>手順

### <a name="create-new-unity-project"></a>新しい Unity プロジェクトを作成します

1. Unity を起動します。
2. **[新規]** を選択します。
![Lesson1 Chapter1 Step2](images/Lesson1Chapter1Step2.JPG)
3. プロジェクト名を入力します (例: "MixedRealityBase")。
![Lesson1 Chapter1 Step3](images/Lesson1Chapter1Step3.JPG)
4. プロジェクトを保存する場所を入力します。
![Lesson1 Chapter1 Step4](images/Lesson1Chapter1Step4.JPG)
5. プロジェクトが **[3D]** に設定されていることを確認します。
![Lesson1 Chapter1 Step5](images/Lesson1Chapter1Step5.JPG)
6. **[プロジェクトの作成]** をクリックします。
![Lesson1 Chapter1 Step6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality 用に Unity プロジェクトを構成する

1. [ファイル] > [ビルド設定] の順に移動して、ビルド設定ウィンドウを開きます。
![Lesson1 Chapter4 Step1](images/Lesson1Chapter4Step1.JPG)
2. [ユニバーサル Windows プラットフォーム] を選択して [ユニバーサル Windows プラットフォーム] に切り替えてから、[プラットフォームの切り替え] ボタンをクリックしてプラットフォームを切り替えます。 HoloLens 2 でアプリを実行するには、ユニバーサル Windows プラットフォーム (UWP) である必要があります。
![Lesson1 Chapter4 Step2](images/Lesson1Chapter4Step2.JPG)
3. 下の図に示されているように、ビルド ウィンドウで [プレーヤー設定] をクリックして仮想現実を有効にしてから、[インスペクター] パネルの [XR 設定] の下の [仮想現実のサポート] チェック ボックスをオンにします。 [インスペクター] パネルを表示するためには、邪魔にならないように [ビルド設定] ウィンドウをドラッグする必要がある場合があることに注意してください。 [仮想現実のサポート] チェック ボックスは、立体視 (それぞれの目で異なる画像をレンダリングする) を有効にすることを指すため、Mixed Reality / AR ヘッドセットにも適用されます。![Lesson1 Chapter4 Step3](images/Lesson1Chapter4Step3.JPG)
4. 同じ [インスペクター] パネルで、[公開設定] の下の [機能] セクションの [空間認知] チェック ボックスがオンになっていることを確認します。 [空間認知] を使用すると、HoloLens 2 などの Mixed Reality デバイスで空間マッピングのメッシュを視覚化できます。 [公開設定] は、[インスペクター] パネルの [XR 設定] の上、[その他の設定] の下にあります。
![Lesson1 Chapter4 Step4](images/Lesson1Chapter4Step4.JPG)

> 注: このセクションでは使用していませんが、有効にできるその他の一般的な機能には、[マイク] (音声コマンド用) と [InternetClient] (ネットワーク接続が必要なサービスの接続用) が含まれています

### <a name="import-the-mixed-reality-toolkit"></a>Mixed Reality ツールキットをインポートする

1. [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) の Unity パッケージをダウンロードし、PC 上のフォルダーに保存します。

2. [アセット] > [インポート] > [カスタム パッケージ] の順にクリックして、Mixed Reality Toolkit パッケージをインポートします。 手順 1 でダウンロードした Mixed Reality Toolkit パッケージを見つけて開き、インポート プロセスを開始します。 インポート プロセスには数分お待ちください。
    ![Lesson1 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Lesson1 Chapter2 Step2b](images/Lesson1Chapter2Step2b.JPG)

3. 次のポップアップ ウィンドウで、[インポート] をクリックして Mixed Reality Toolkit のインポートを開始します。 図に示されているように、すべての項目を必ずオンにしてください。 Mixed Reality Toolkit の既定の設定を適用するよう求めるポップアップ ダイアログ ボックスを表示されたら、[適用] をクリックします。
    ![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3.JPG) ![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Mixed Reality ツールキットを構成する

1. メニュー バーで [Mixed Reality Toolkit] > [構成] の順に選択して、Mixed Toolkit を構成します。 Mixed Reality Toolkit をインポートした後でこのメニュー項目が表示されない場合は、Unity を再起動してください。
![Lesson1 Chapter3 Step1](images/Lesson1Chapter3Step1.JPG)
2. これでシーンに、いくつかの新しい項目と、Mixed Reality Toolkit からの変更が表示されます。 [ファイル] > [名前を付けて保存] の順にクリックして別の名前でシーンを保存し、シーンに名前を付けます (例: BaseScene)。 プロジェクトのアセット フォルダー内の [シーン] フォルダーにシーンを保存することで、シーンを整理します。
![Lesson1 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
![Lesson1 Chapter3 Step2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>デバイスへのアプリケーションのビルド

1. 前のセクションで [ビルド設定] ウィンドウを閉じた場合は、[ファイル] > [ビルド設定] の順に移動して [ビルド設定] ウィンドウを再度開きます。
    ![Lesson1 Chapter5 Step1](images/Lesson1Chapter5Step1.JPG)

2. [開いているシーンの追加] ボタンをクリックして、試したいシーンが [ビルド内のシーン] リストに含まれていることを確認します。

3. [ビルド] ボタンを押して、ビルド プロセスを開始します。
    ![Lesson1 Chapter5 Step3](images/Lesson1Chapter5Step3.JPG)

4. アプリケーション用の新しいフォルダーを作成して、名前を付けます。 下の図では、アプリケーションを含めるために [App] という名前のフォルダーが作成されています。 [フォルダーの選択] をクリックして、新しく作成したフォルダーへのビルドを開始します。 ビルドが完了したら、Unity の [ビルド設定] ウィンドウを閉じてもかまいません。 
    ![Lesson1 Chapter5 Step4](images/Lesson1Chapter5Step4.JPG)

  > 注: ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。 [エラー:CS0246 = “XX” という名前の型または名前空間が見つかりませんでした (ディレクトリの使用またはアセンブリ参照が不足しています)] のようなエラーが表示される場合は、[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) のインストールが必要な場合があります
  >

5. ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。 [MixedRealityBase.sln] ソリューション (または、プロジェクトの代替名を使用した場合は対応する名前) をダブルクリックして、Visual Studio でソリューション ファイルを開きます。

  > 注:必ず、新しく作成したフォルダー (つまり、前の手順で名前付け規則に従っている場合は、[App] フォルダー) を開いてください。そのフォルダーの外部に同じような名前の .sln ファイルがあり、ビルド フォルダー内の .sln ファイルと混同してはならないためです。 

![Lesson1 Chapter5 Step5](images/Lesson1Chapter5Step5.JPG)

  > 注:Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、[「ツールのインストール」ページ](install-the-tools.md)で示されている、前提条件となるすべてのコンポーネントがインストールされていることを確認してください

6. USB ケーブルを使って HoloLens 2 を PC に接続します。 これらのレッスンの手順では、HoloLens 2 デバイスを使ってテストをデプロイすることを前提としていますが、[HoloLens 2 エミュレーター](using-the-hololens-emulator.md)にデプロイすることも、[サイドローディング用のアプリ パッケージ](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)を作成することもできます

7. デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。 HoloLens 2 に初めてデプロイする場合は、Visual Studio により、PIN を使用して HoloLens 2 をペアリングするよう求められる場合があります。 開発者モードを有効にするか、Visual Studio とペアリングする必要がある場合は、[こちらの手順](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)に従ってください。

8. [リリース] 構成と [ARM] アーキテクチャを選択して、HoloLens 2 へのビルド用に Visual Studio を構成します。
    ![Lesson1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. 最後の手順は、[デバッグ] > [デバッグなしで開始] を選択して、デバイスにビルドすることです。 [デバッグなしで開始] を選択すると、ビルドが成功した時点でアプリケーションがデバイスですぐに起動しますが、Visual Studio にデバッグ情報は表示されません。 これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。 また、[ビルド] > [ソリューションの配置] を選択することで、アプリケーションを自動的に起動せずにデバイスに配置することもできます。
    ![Lesson1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>結論

これで、最初の HoloLens 2 アプリケーションがデプロイされました。 手順に従うと、HoloLens 2 によって認識されたすべてのサーフェイスをカバーする空間のメッシュが表示されるはずです。 さらに、手の追跡用の手と指のインジケーターと、アプリのパフォーマンスを監視するためのフレームレート カウンターも表示されるはずです。 これらは、Mixed Reality ツールキットに含まれている、すぐに使用できる基礎となる部分のほんの一部です。 以降のレッスンでは、HoloLens 2 と Mixed Reality Toolkit の機能を十分に検討できるように、シーンへのコンテンツや対話機能の追加を始めます。

>注:音声コマンドを使用してフレームレート カウンターを切り替える方法については、[レッスン 5](mrlearning-base-ch5.md) で説明します

[次のレッスン: ユーザー インターフェイス、手の追跡、Mixed Reality Toolkit の構成](mrlearning-base-ch2.md)
