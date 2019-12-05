---
title: 入門チュートリアル -2. プロジェクトと最初のアプリケーションの初期化
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Unity, チュートリアル, Hololens
ms.openlocfilehash: d4e58e2c9236ba35b4394fd80cde3843edaa6f57
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491204"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. プロジェクトと最初のアプリケーションの初期化

この最初のレッスンでは、[Mixed Reality ツールキット (MRTK) ]()によって提供され、HoloLens 2 用の最初のアプリケーションを起動してデバイスにデプロイされる必要のあるいくつかの機能について学習します。

## <a name="objectives"></a>目標

* HoloLens 用 Unity の開発を最適化する。
* アセットをインポートし、シーンをセットアップする。
* 空間マッピングのメッシュ、ハンド メッシュ、およびフレームレート カウンターの視覚化。

## <a name="instructions"></a>手順

### <a name="create-new-unity-project"></a>新しい Unity プロジェクトを作成します

1. Unity を起動します。
2. **[新規]** を選択します。
![レッスン 1 セクション 1 手順 2](images/mrlearning-base-ch1-1-step2.JPG)

3. プロジェクト名を入力します (例: "MixedRealityBase")。
![レッスン 1 セクション 1 手順 3](images/mrlearning-base-ch1-1-step3.JPG)
4. プロジェクトを保存する場所を入力します。
![レッスン 1 セクション 1 手順 4](images/mrlearning-base-ch1-1-step4.JPG)
5. プロジェクトが **[3D]** に設定されていることを確認します。
![レッスン 1 セクション 1 手順 5](images/mrlearning-base-ch1-1-step5.JPG)
6. **[プロジェクトの作成]** をクリックします。
![レッスン 1 セクション 1 手順 6](images/mrlearning-base-ch1-1-step6.JPG)


### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality 用に Unity プロジェクトを構成する

1. **[ファイル]**  >  **[ビルド設定]** の順に移動して、 *[ビルド設定]* ウィンドウを開きます。
![レッスン 1 セクション 2 手順 1](images/mrlearning-base-ch1-2-step1.JPG)
2. *[ユニバーサル Windows プラットフォーム ]* を選択して、 **[Switch Platform]\(プラットフォームの切り替え\)** ボタンをクリックしてプラットフォームを切り替えます。 HoloLens 2 上で実行されるアプリケーションは、ユニバーサル Windows プラットフォーム (UWP) に対応している必要があります。
![レッスン 1 セクション 2 手順 2](images/mrlearning-base-ch1-2-step2.JPG)
3. 下の図に示されているように、ビルド ウィンドウで **[プレーヤー設定]** ボタンをクリックして仮想現実を有効にしてから、[インスペクター] パネルの [XR 設定] 下にある *[仮想現実のサポート]* チェック ボックスをオンにします。 状況によっては、[インスペクター] パネルを表示するために、邪魔にならないように *[ビルド設定]* ウィンドウをドラッグする必要があることに注意してください。 *[仮想現実のサポート]* チェック ボックスは、立体視 (それぞれの目で異なる画像をレンダリングする) を有効にすることを指すため、Mixed Reality および Augmented Reality ヘッドセットにも適用されます。![レッスン 1 セクション 2 手順 3](images/mrlearning-base-ch1-2-step3.JPG)
4. また、[XR の設定] 下で *[Stereo Rendering Mode]\(ステレオ レンダリング モード\)* を *[Single Pass Instanced]\(単一パスのインスタンス化\)* に変更します。 この[パイプラインのレンダリング スタイル](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)は通常、HoloLens 2 においてパフォーマンスが最も高くなります。 Unity 環境における他の高パフォーマンスの構成に関心がある場合は、[こちらの手順](recommended-settings-for-unity.md)に従ってください。
![レッスン 1 セクション 2 手順 4](images/mrlearning-base-ch1-2-step4.jpg)
5. 同じ [インスペクター] パネルで、 *[公開設定]* の下の [機能] セクションにある *[空間認識]* チェック ボックスがオンになっていることを確認します。 空間認識を使用すると、HoloLens 2 などの Mixed Reality デバイス上で空間マッピングのメッシュを視覚化できます。 [公開設定] は、[インスペクター] パネル内の [XR 設定] の上、[その他の設定] の下にあります。
![レッスン 1 セクション 2 手順 5](images/mrlearning-base-ch1-2-step5.JPG)

    > [!NOTE]
    > このセクションでは使用していませんが、有効にできるその他の一般的な機能には、 *[マイク]* (音声コマンド用) と *[InternetClient]* (ネットワーク接続が必要なサービスの接続用) が含まれています。

### <a name="import-the-mixed-reality-toolkit"></a>Mixed Reality ツールキットをインポートする

1. [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) の Unity [ Foundation パッケージ バージョン 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) をダウンロードし、PC 上のフォルダーに保存します。

2. 前の手順でダウンロードした *Mixed Reality Toolkit* パッケージをインポートします。 まず、 **[資産]**  >  **[インポート]**  >  **[カスタム パッケージ]** の順にクリックし、*Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* を選択して開き、インポート処理を開始します。 インポート プロセスが完了するまで数分間、待機してください。
    ![レッスン 1 セクション 3 手順 2a](images/mrlearning-base-ch1-3-step2a.JPG) ![レッスン 1 セクション 3 手順 2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. 次のポップアップ ウィンドウで、 **[インポート]** をクリックして、選択したパッケージの Unity プロジェクトへのインポートを開始します。 図に示されているように、すべての項目のチェックを必ずオンにしてください。
    ![レッスン 1 セクション 3 手順 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > Mixed Reality Toolkit の既定の設定を適用するかを尋ねるポップアップのダイアログ ボックスが表示されたら、 **[適用]** をクリックします。 MRTK では、自動セットアップのためにインポートが行われる場合、不足している推奨設定についてプロジェクトが分析されます。 設定によっては、ポップアップ表示は、以下の図と異なる場合があります。

    ![レッスン 1 セクション 3 手順 4 注意 1](images/mrlearning-base-ch1-3-step4-note1.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Mixed Reality ツールキットを構成する

1. **[Mixed Reality Toolkit]**  >  **[Add to Scene and Configure..]\(シーンに追加して構成する\)** の順に選択して、 *[Mixed reality Toolkit]* を現在のシーンに追加します。 メニュー バーから行います。 Mixed Reality Toolkit をインポートした後でこのメニュー項目が表示されない場合は、Unity を再起動してください。
    ![レッスン 1 セクション 4 手順 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > [Mixed Reality Toolkit 向けのプロファイル](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)を選択するためのポップアップ ダイアログ ボックスが表示される場合があります。 *DefaultHoloLens2ConfigurationProfile* という名前のプロファイルをダブルクリックして選択します。

2. シーンには、新しい項目と変更がいくつか追加される予定です。 **[ファイル]**  >  **[名前を付けて保存]** の順にクリックして別の名前でシーンを保存します。シーンには、*BaseScene* などの名前を付けます。 シーンをプロジェクトの *[アセット]* フォルダー内の *[シーン]* フォルダーに保存して、整理します。
    ![レッスン 1 セクション 4 手順 2a](images/mrlearning-base-ch1-4-step2a.JPG) ![レッスン 1 セクション 4 手順 2b](images/mrlearning-base-ch1-4-step2b.JPG)

### <a name="build-your-application-to-your-device"></a>デバイスへのアプリケーションのビルド

1. 前のセクションで *[ビルド設定]* ウィンドウを閉じた場合は、 **[ファイル]**  >  **[ビルド設定]** の順に移動して *[ビルド設定]* ウィンドウを再度開きます。
    ![レッスン 1 セクション 5 手順 1](images/mrlearning-base-ch1-5-step1.JPG)

2. Unity でシーンが開いているときに、 **[Add Open Scenes]\(開いているシーンの追加\)** ボタンをクリックして、 *[Scenes in Build]\(ビルド内のシーン\)* に先ほど作成したシーンがあることを確認します。

3. **[ビルド]** ボタンを押して、ビルド プロセスを開始します。
    ![レッスン 1 セクション 5 手順 3](images/mrlearning-base-ch1-5-step3.JPG)

4. アプリケーション用の新しいフォルダーを作成して、名前を付けます。 下の図では、アプリケーションを格納するための App という名前のフォルダーが作成されています。 **[フォルダーの選択]** をクリックして、新しく作成したフォルダーへのビルドを開始します。 ビルドが完了したら、Unity の *[ビルド設定]* ウィンドウを閉じてもかまいません。
    ![レッスン 1 セクション 5 手順 4](images/mrlearning-base-ch1-5-step4.JPG)

  > [!IMPORTANT]
  > ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。 "エラー:CS0246 = “XX” という名前の型または名前空間が見つかりませんでした (using ディレクティブまたはアセンブリ参照が不足しています)" のようなエラーが表示される場合があります。 その場合は、必要に応じて [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk) をインストールします。

5. ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。 *MixedRealityBase.sln* ソリューション (または、プロジェクトの代替名を使用した場合は対応する名前) をダブルクリックして、Visual Studio でソリューション ファイルを開きます。

    > [!NOTE]
    > 必ず、新しく作成したフォルダー (つまり、前の手順での名前付け規則に従っている場合は、*App* フォルダー) を開いてください。そのフォルダーの外部に同じような名前の .sln ファイルがあり、ビルド フォルダー内の .sln ファイルと混同しないようにするためです。 フォルダー構造は、以下の画像のようになります。
    >
    > Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、[「ツールのインストール」ページ](install-the-tools.md)で示されている、前提条件となるすべてのコンポーネントがインストールされていることを確認してください

    ![レッスン 1 セクション 5 手順 5](images/mrlearning-base-ch1-5-step5.JPG)

6. HoloLens 2 を PC に接続します。 これらの手順では、HoloLens 2 デバイスにデプロイすることを前提としていますが、[HoloLens 2 エミュレーター](using-the-hololens-emulator.md)にデプロイすることも、[サイドローディング用のアプリ パッケージ](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)を作成することもできます

    > [!IMPORTANT]
    > デバイスをビルドする前に、デバイスが "*開発者モード*" であり、かつ、開発コンピューターと一組になっている必要があります。 この両方のステップを完了するには、[こちらの手順](using-visual-studio.md)に従います。

7. *[リリース]* または *[マスター]* 構成、 *[ARM]* アーキテクチャ、ターゲットとして *[デバイス]* を選択して、HoloLens 2 に対するビルド用に Visual Studio を構成します。
    ![レッスン 1 セクション 5 手順 8](images/mrlearning-base-ch1-5-step7.JPG)

8. 最後の手順として、 **[デバッグ]**  >  **[デバッグなしで開始]** を選択してビルドし、デバイスにデプロイします。 *[デバッグなしで開始]* を選択すると、ビルドが成功した時点でアプリケーションがデバイス上ですぐに起動しますが、デバッガーがアタッチされていない状態であり、Visual Studio にデバッグ情報は表示されません。 これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。

    > [!NOTE]
    > また、 **[ビルド]**  >  **[ソリューションの配置]** を選択することで、アプリケーションを自動的に起動せずにデバイスにデプロイすることもできます。

    ![レッスン 1 セクション 5 手順 9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>結論

これで、最初の HoloLens 2 アプリケーションがデプロイされました。 手順に従うと、HoloLens 2 によって認識されたすべてのサーフェイスに対応する空間マッピングのメッシュが表示されるはずです。 さらに、ハンド トラッキング用の手および指に対するインジケーターと、アプリケーションのパフォーマンスを監視するためのフレーム レート カウンターも表示されるはずです。 これらは、Mixed Reality ツールキットに含まれている、すぐに使用できる基礎となる部分のほんの一部です。 以降のレッスンでは、HoloLens 2 と Mixed Reality Toolkit の機能を十分に探索できるように、シーンにコンテンツや対話機能を追加する作業を開始します。

> [!NOTE]
> アプリ上で、ビジュアル プロファイラーに気が付く場合があります。 音声コマンドを使用してフレーム レート カウンターを切り替える方法については、[レッスン 5](mrlearning-base-ch5.md) で説明します。 一般に、コードの変更によってパフォーマンスが影響を受ける可能性がある場合は、開発中に常にビジュアル プロファイラーを表示したままにしておくことをお勧めします。 HoloLens 2 アプリケーションは、[60 FPS で継続的に実行される](understanding-performance-for-mixed-reality.md)必要があります。

[次のレッスン:3.ユーザー インターフェイスの作成と Mixed Reality ツールキットの構成](mrlearning-base-ch2.md)
