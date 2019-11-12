---
title: 入門チュートリアル-2. プロジェクトと最初のアプリケーションを初期化しています
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 3bf218b42ea8abed45a80c0dd048e791cdd8372b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926885"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. プロジェクトと最初のアプリケーションを初期化する

この最初のレッスンでは、 [Mixed Reality Toolkit (MRTK)]()が提供する必要があるいくつかの機能について説明します。 HoloLens 2 の最初のアプリケーションを起動し、デバイスにデプロイします。

## <a name="objectives"></a>目標

* HoloLens 用 Unity の開発を最適化する。
* アセットをインポートし、シーンをセットアップする。
* 空間マッピングメッシュ、手メッシュ、フレームレートカウンターの視覚化。

## <a name="instructions"></a>手順

### <a name="create-new-unity-project"></a>新しい Unity プロジェクトを作成します

1. Unity を起動します。
2. **[新規]** を選択します。
![レッスン1から Section1 のステップ](images/mrlearning-base-ch1-1-step2.JPG)

3. プロジェクト名を入力してください (例: "MixedRealityBase")。
![レッスン1から Section1 手順 3](images/mrlearning-base-ch1-1-step3.JPG)
4. プロジェクトを保存する場所を入力します。
![レッスン1から Section1 手順 4](images/mrlearning-base-ch1-1-step4.JPG)
5. プロジェクトが **[3D]** に設定されていることを確認します。
![レッスン1から Section1 手順 5](images/mrlearning-base-ch1-1-step5.JPG)
6. **[プロジェクトの作成]** をクリックします。
![レッスン1から Section1 手順 6](images/mrlearning-base-ch1-1-step6.JPG)


### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality 用に Unity プロジェクトを構成する

1. [*ビルドの設定*] ウィンドウを開き、[**ファイル** > **ビルドの設定**] に移動します。
![レッスン1から Section2 ステップ](images/mrlearning-base-ch1-2-step1.JPG)
2. *ユニバーサル Windows プラットフォーム*を選択し、 **[プラットフォームの切り替え]** ボタンをクリックしてプラットフォームを切り替えます。 HoloLens 2 で実行されるアプリケーションは、ユニバーサル Windows プラットフォーム (UWP) と互換性がある必要があります。
![レッスン1から Section2 のステップ](images/mrlearning-base-ch1-2-step2.JPG)
3. 次の図に示すように、ビルド] ウィンドウの **[プレーヤーの設定]** ボタンをクリックして仮想現実を有効にし、[XR の設定 の下の [*仮想*化の詳細] チェックボックスをオンにします。 [インスペクター] パネルを表示するには、[*ビルドの設定*] ウィンドウをそのままドラッグする必要があることに注意してください。 [*サポートされている仮想現実*] チェックボックスは、ステレオスコピック構想の有効化 (各目に異なるイメージのレンダリング ![) を参照するため、Mixed reality と拡張された現実のヘッドセットにも適用され](images/mrlearning-base-ch1-2-step3.JPG)
4. また、[XR の設定] で、*ステレオレンダリングモード*を*シングルパスインスタンス*化に変更します。 通常、この[表示パイプラインスタイル](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)は HoloLens 2 で最も高いパフォーマンスを備えています。 Unity 環境の他のパフォーマンスの高い構成に関心がある場合は、こちらの[手順](recommended-settings-for-unity.md)に従ってください。
![レッスン1から Section2 手順 4](images/mrlearning-base-ch1-2-step4.jpg)
5. 同じ [インスペクター] パネルで、[機能] セクションの [*空間認識*] チェックボックスが [*発行の設定*] で有効になっていることを確認します。 空間認識を使用すると、HoloLens 2 などの混合の現実デバイスで空間マッピングメッシュを視覚化できます。 発行の設定は、[インスペクター] パネルの [XR Settings (その他の設定)] の下にあります。
![レッスン1から Section2 手順 5](images/mrlearning-base-ch1-2-step5.JPG)

    > [!NOTE]
    > このセクションでは使用しませんが、他のいくつかの一般的な機能を有効にするには、音声コマンドの*マイク*や、ネットワーク接続を必要とするサービスに接続するための*internetclient*などがあります。

### <a name="import-the-mixed-reality-toolkit"></a>Mixed Reality ツールキットをインポートする

1. [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation パッケージバージョン 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)をダウンロードし、PC 上のフォルダーに保存します。

2. 前の手順でダウンロードした*Mixed Reality Toolkit*パッケージをインポートします。 まず、 **[アセット]** をクリックし > **カスタムパッケージ** > **インポート**し、 *unitypackage*を選択して開き、インポートプロセスを開始します。 インポート処理が完了するまで数分かかります。
    ![レッスン1から Section3 Step2a](images/mrlearning-base-ch1-3-step2a.JPG) ![レッスン1から Section3 Step2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. 次のポップアップウィンドウで、 **[インポート]** をクリックして、選択したパッケージの Unity プロジェクトへのインポートを開始します。 画像に示されているように、すべての項目がオンになっていることを確認します。
    ![レッスン1から Section3 手順 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > Mixed Reality Toolkit の既定の設定を適用するよう求めるポップアップダイアログボックスが表示されたら、 **[適用]** をクリックします。 MRTK では、自動セットアップのためにインポートするときに、推奨されていない設定があればプロジェクトを分析します。 設定によっては、次の図のようなポップアップが表示される場合があります。

    ![レッスン1から Section3 手順 4 Note1](images/mrlearning-base-ch1-3-step4-note1.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Mixed Reality ツールキットを構成する

1. Mixed **reality** toolkit を選択して、現在のシーンに*mixed reality toolkit*を追加し > [**シーンに追加] および [構成] を選択します**。 メニューバーから。 Mixed Reality Toolkit をインポートした後でこのメニュー項目が表示されない場合は、Unity を再起動してください。
    ![レッスン1から Section4 ステップ](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > [Mixed Reality Toolkit のプロファイル](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)を選択するためのポップアップダイアログボックスが表示される場合があります。 *DefaultHoloLens2ConfigurationProfile*という名前のプロファイルをダブルクリックして選択します。

2. シーンに新しい項目と変更がいくつか追加されます。 [**ファイル** > 名前を付け**て保存...** ] をクリックしてシーンを別の名前で保存し、シーンに*basescene*などの名前を付けます。 シーンを整理して、プロジェクトの [ *Assets* ] フォルダー内の [*シーン*] フォルダーに保存します。
    ![レッスン1から Section4 Step2a](images/mrlearning-base-ch1-4-step2a.JPG) ![レッスン1から Section4 Step2b](images/mrlearning-base-ch1-4-step2b.JPG)

### <a name="build-your-application-to-your-device"></a>デバイスへのアプリケーションのビルド

1. 前のセクションの [*ビルドの設定*] ウィンドウを閉じた場合は、[**ファイル** > ビルドの**設定**] に移動して [ビルドの*設定*] ウィンドウを再び開きます。
    ![レッスン1から Section5 ステップ](images/mrlearning-base-ch1-5-step1.JPG)

2. 作成したシーンが、Unity でシーンが開いているときに [開いているシーンを**追加**] ボタンをクリックして、[ビルド] の一覧*の*シーンにあることを確認します。

3. ビルドを開始するには、 **[ビルド]** をクリックします。
    ![レッスン1から Section5 手順 3](images/mrlearning-base-ch1-5-step3.JPG)

4. アプリケーション用の新しいフォルダーを作成して、名前を付けます。 次の図では、アプリケーションを格納するために、App という名前のフォルダーが作成されています。 **[フォルダーの選択]** をクリックして、新しく作成したフォルダーへのビルドを開始します。 ビルドが完了したら、Unity の [*ビルドの設定*] ウィンドウを閉じることができます。
    ![レッスン1から Section5 手順 4](images/mrlearning-base-ch1-5-step4.JPG)

  > [!IMPORTANT]
  > ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。 "エラー: CS0246 = 型または名前空間の名前" XX "が見つからないなどのエラーが表示された場合は、using ディレクティブまたはアセンブリ参照が不足しています。 その場合は、 [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)のインストールが必要になることがあります。

5. ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。 *MixedRealityBase*ソリューションをダブルクリックするか、プロジェクトに別の名前を使用している場合は対応する名前をダブルクリックして、Visual Studio でソリューションファイルを開きます。

    > [!NOTE]
    > 新しく作成されたフォルダー (前の手順の名前付け規則に従っている場合は*アプリ*フォルダー) を必ず開いてください。これは、ビルドフォルダー内の .sln ファイルと混同しないように、同じ名前の .sln ファイルがそのフォルダー外に存在するためです。 フォルダー構造は次の図のようになります。
    >
    > Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、[「ツールのインストール」ページ](install-the-tools.md)で示されている、前提条件となるすべてのコンポーネントがインストールされていることを確認してください

    ![レッスン1から Section5 手順5](images/mrlearning-base-ch1-5-step5.JPG)

6. HoloLens 2 を PC に接続します。 これらの手順では HoloLens 2 デバイスにデプロイすることを前提としていますが、 [hololens 2 エミュレーター](using-the-hololens-emulator.md)にデプロイするか、[サイドローディング用のアプリパッケージの](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)作成を選択することもできます。

    > [!IMPORTANT]
    > デバイスをビルドする前に、デバイスが開発*者モード*であり、開発用コンピューターとペアリングされている必要があります。 これらの手順は、次[の手順に従って](using-visual-studio.md)完了できます。

7. *リリース*または*マスター*構成、 *ARM*アーキテクチャ、および*デバイス*をターゲットとして選択して、HoloLens 2 にビルドするように Visual Studio を構成します。
    ![レッスン1から Section5 Step8](images/mrlearning-base-ch1-5-step7.JPG)

8. 最後の手順は、**デバッグ > デバッグ** **なしで開始** を選択して、デバイスにビルドしてデプロイすることです。 [*デバッグなしで開始*] を選択すると、ビルドが成功したときに、アプリケーションがすぐにデバイスで開始されます。ただし、デバッガーがアタッチされていない場合は、Visual Studio に情報が表示されます。 これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。

    > [!NOTE]
    > また、[**ビルド** > **デプロイ**] を選択して、アプリケーションを自動的に起動せずにデバイスにデプロイすることもできます。

    ![レッスン1から Section5 Step9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>結論

これで、最初の HoloLens 2 アプリケーションが展開されました。 このチュートリアルでは、HoloLens 2 によって認識されたすべてのサーフェスをカバーする空間マッピングメッシュがあることを確認します。 さらに、ハンドトラッキングのためのインジケーターと、アプリケーションのパフォーマンスを監視するためのフレームレートカウンターが表示されます。 これらは、Mixed Reality ツールキットに含まれている、すぐに使用できる基礎となる部分のほんの一部です。 このレッスンでは、HoloLens 2 と Mixed Reality Toolkit の機能を十分に調べることができるように、シーンにコンテンツと対話機能を追加します。

> [!NOTE]
> アプリでは、ビジュアルプロファイラーに気付くことがあります。 [レッスン 5](mrlearning-base-ch5.md)では、音声コマンドを使用してフレームレートカウンターを切り替える方法について説明します。 一般に、コードの変更によってパフォーマンスが低下した可能性がある場合は、開発中に常にビジュアルプロファイラーを表示したままにしておくことをお勧めします。 HoloLens 2 アプリケーションは、 [60 FPS で継続的に実行](understanding-performance-for-mixed-reality.md)する必要があります。

[次のレッスン: 3. ユーザーインターフェイスを作成し、Mixed Reality Toolkit を構成する](mrlearning-base-ch2.md)
