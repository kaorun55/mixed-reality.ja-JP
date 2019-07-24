---
title: ML 学習ベース モジュール - プロジェクトの初期化と最初のアプリケーション
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 51cfc123f7da8d25a53eecfb730f60cf10fe7377
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387785"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. プロジェクトと最初のアプリケーションを初期化しています

この最初のレッスンでは、Mixed Reality Toolkit (MRTK) が提供する必要があるいくつかの機能について説明します。 HoloLens 2 の最初のアプリケーションを起動し、デバイスにデプロイします。

## <a name="objectives"></a>目的

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

1. [ビルドの設定] ウィンドウを開き、[ファイル > ビルドの設定] に移動します。
![Lesson1 Chapter4 Step1](images/Lesson1Chapter4Step1.JPG)
2. [ユニバーサル Windows プラットフォーム] を選択して、ユニバーサル Windows プラットフォームに切り替えます。 [プラットフォームの切り替え] ボタンをクリックして、プラットフォームを切り替えます。 HoloLens 2 で実行されるアプリケーションは、ユニバーサル Windows プラットフォーム (UWP) と互換性がある必要があります。
![Lesson1 Chapter4 Step2](images/Lesson1Chapter4Step2.JPG)
3. 次の図に示すように、[ビルド] ウィンドウで [プレーヤーの設定] をクリックし、[XR の設定] の下にある [Virtual Reality がサポートする] チェックボックスをオンにして、仮想現実を有効にします。 [インスペクター] パネルを表示するには、[ビルドの設定] ウィンドウをそのままドラッグする必要があることに注意してください。 [サポートされている仮想現実] チェックボックスは、混合現実と拡張された現実のヘッドセットにも適用されます。これは、ステレオスコピック構想の有効化 (各視点に異なるイメージをレンダリングする) を指しているためです。![Lesson1 Chapter4 Step3](images/Lesson1Chapter4Step3.JPG)
4. 同じ [インスペクター] パネルで、[機能] セクションの [空間認識] チェックボックスが [発行の設定] で有効になっていることを確認します。 空間認識を使用すると、HoloLens 2 などの混合の現実デバイスで空間マッピングメッシュを視覚化できます。 発行の設定は、[インスペクター] パネルの [XR Settings (その他の設定)] の下にあります。
![Lesson1 Chapter4 Step4](images/Lesson1Chapter4Step4.JPG)

> 注: このセクションでは使用しませんが、他のいくつかの一般的な機能を有効にするには、音声コマンドのマイクや、ネットワーク接続を必要とするサービスに接続するための InternetClient などがあります。

### <a name="import-the-mixed-reality-toolkit"></a>Mixed Reality ツールキットをインポートする

1. [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) Unity パッケージをダウンロードし、PC 上のフォルダーに保存します。

2. [アセット] > [インポート] > [カスタム パッケージ] の順にクリックして、Mixed Reality Toolkit パッケージをインポートします。 手順 1 でダウンロードした Mixed Reality Toolkit パッケージを見つけて開き、インポート プロセスを開始します。 インポート プロセスには数分お待ちください。
    ![Lesson1 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Lesson1 Chapter2 Step2b](images/Lesson1Chapter2Step2b.JPG)

3. 次のポップアップウィンドウで、[インポート] をクリックして、Mixed Reality Toolkit のインポートを開始します。 画像に示されているように、すべての項目がオンになっていることを確認します。 Mixed Reality Toolkit の既定の設定を適用するよう求めるポップアップダイアログボックスが表示されたら、[適用] をクリックします。
    ![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3.JPG) ![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Mixed Reality ツールキットを構成する

1. メニューバーから [Mixed Reality Toolkit > 構成] を選択して、MRTK を構成します。 Mixed Reality Toolkit をインポートした後でこのメニュー項目が表示されない場合は、Unity を再起動してください。
  ![Lesson1 Chapter3 Step1](images/Lesson1Chapter3Step1.JPG)

  > 注:Mixed Reality Toolkit のプロファイルを選択するよう求めるポップアップダイアログボックスが表示される場合があります。 その場合は、[Ok] を選択し、"DefaultMixedRealityToolkitConfigurationProfile" という名前のプロファイルを選択します。

2. シーンには、MRTK からいくつかの新しい項目と変更が加えられています。 [ファイル > 名前を付けて保存] をクリックし、シーンに BaseScene などの名前を付けて、シーンを別の名前で保存します。 シーンを整理して、プロジェクトの [Assets] フォルダー内の [シーン] フォルダーに保存します。
  ![Lesson1 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
  ![Lesson1 Chapter3 Step2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>デバイスへのアプリケーションのビルド

1. 前のセクションの [ビルドの設定] ウィンドウを閉じた場合は、[ファイル > ビルドの設定] に移動して [ビルドの設定] ウィンドウを再び開きます。
    ![Lesson1 Chapter5 Step1](images/Lesson1Chapter5Step1.JPG)

2. [開いているシーンを追加] ボタンをクリックして、目的のシーンがビルドリストのシーンにあることを確認します。

3. [ビルド] ボタンを押して、ビルド プロセスを開始します。
    ![Lesson1 Chapter5 Step3](images/Lesson1Chapter5Step3.JPG)

4. アプリケーション用の新しいフォルダーを作成して、名前を付けます。 次の図では、アプリケーションを格納するために、App という名前のフォルダーが作成されています。 [フォルダーの選択] をクリックして、新しく作成したフォルダーへのビルドを開始します。 ビルドが完了したら、Unity の [ビルドの設定] ウィンドウを閉じることができます。 
    ![Lesson1 Chapter5 Step4](images/Lesson1Chapter5Step4.JPG)

  > 注: ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。 次のようなエラーが表示された場合:CS0246 = 型または名前空間の名前 "XX" が見つかりませんでした。 using ディレクティブまたはアセンブリ参照が指定されていないことを確認してください。 その場合は、 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)のインストールが必要になることがあります。
  >

5. ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。 MixedRealityBase ソリューションをダブルクリックするか、プロジェクトに別の名前を使用している場合は対応する名前をダブルクリックして、Visual Studio でソリューションファイルを開きます。

  > 注:新しく作成されたフォルダー (前の手順の名前付け規則に従っている場合は、アプリフォルダー) を必ず開いてください。これは、ビルドフォルダー内の .sln ファイルと混同しないように、そのフォルダーの外部にある同じ名前の .sln ファイルが存在するためです。 

![Lesson1 Chapter5 Step5](images/Lesson1Chapter5Step5.JPG)

  > 注:Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、[「ツールのインストール」ページ](install-the-tools.md)で示されている、前提条件となるすべてのコンポーネントがインストールされていることを確認してください

6. HoloLens 2 を PC に接続します。 これらの手順では、HoloLens 2 デバイスでテストをデプロイすることを前提としていますが、 [hololens 2 エミュレーター](using-the-hololens-emulator.md)にデプロイするか、[サイドローディング用のアプリパッケージの](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)作成を選択することもできます。

7. デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。 初めて HoloLens 2 にデプロイする場合、Visual Studio によって HoloLens 2 と PIN をペアリングするように求めるメッセージが表示されることがあります。 開発者モードを有効にするか、Visual Studio とペアリングする必要がある場合は、[こちらの手順](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)に従ってください。

8. リリース構成と ARM アーキテクチャを選択して、HoloLens 2 にビルドするように Visual Studio を構成します。
    ![Lesson1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. 最後の手順は、デバッグ > デバッグなしで開始 を選択してデバイスにビルドすることです。 [デバッグなしで開始] を選択すると、ビルドが成功したときに、Visual Studio に表示されるデバッグ情報がなくても、アプリケーションは直ちにデバイスで開始されます。 これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。 また、[ビルド > デプロイ] を選択して、アプリケーションを自動的に起動せずにデバイスにデプロイすることもできます。
    ![Lesson1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>結論

これで、最初の HoloLens 2 アプリケーションが展開されました。 このチュートリアルでは、HoloLens 2 によって認識されたすべてのサーフェスをカバーする空間メッシュがあることを確認します。 さらに、ハンドトラッキングのためのインジケーターと、アプリケーションのパフォーマンスを監視するためのフレームレートカウンターが表示されます。 これらは、Mixed Reality ツールキットに含まれている、すぐに使用できる基礎となる部分のほんの一部です。 ここで紹介するレッスンでは、HoloLens 2 と Mixed Reality Toolkit の機能を完全に調べることができるように、コンテンツと対話機能をシーンに追加します。

>注:音声コマンドを使用してフレームレート カウンターを切り替える方法については、[レッスン 5](mrlearning-base-ch5.md) で説明します

[次のレッスン: ユーザー インターフェイス、手の追跡、Mixed Reality Toolkit の構成](mrlearning-base-ch2.md)
