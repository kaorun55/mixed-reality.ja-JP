---
title: 入門チュートリアル -2. プロジェクトと最初のアプリケーションの初期化
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 56adb4bfc66768684c8269c0f0cafd70c486ea8a
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376209"
---
# <a name="2-initializing-your-project-and-first-application"></a>2.プロジェクトと最初のアプリケーションの初期化

## <a name="overview"></a>概要

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
この最初のチュートリアルでは、<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality ツールキット (MRTK) </a>によって提供されるいくつかの機能について学習し、HoloLens 2 用の最初のアプリケーションを起動してデバイスにデプロイします。

## <a name="objectives"></a>目標

* HoloLens 開発用に Unity を構成する
* アセットをインポートし、シーンをセットアップする
* 空間マッピングのメッシュ、ハンド メッシュ、およびフレームレート カウンターを視覚化する

## <a name="prerequisites"></a>前提条件

* 正しい[ツールがインストールされている](install-the-tools.md)構成済みの Windows 10 PC
* Windows 10 SDK 10.0.18362.0 以降
* 基本的な C# プログラミング能力
* [開発用に構成された](using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス
* Unity 2019.2.X がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>

> [!IMPORTANT]
> このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.2.X です。 これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。

## <a name="create-new-unity-project"></a>新しい Unity プロジェクトを作成します

**Unity Hub** を起動し、 **[Projects]\(プロジェクト\)** タブを選択し、 **[New]\(新規\)** ボタンの横にある**下矢印**をクリックします。

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

上の「[前提条件](#prerequisites)」セクションで指定されている Unity のバージョンを選択します。

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

[Create a new project]\(新規プロジェクトの作成\) ウィンドウで、以下のようにします。

* **[Templates]\(テンプレート\)** が **3D** に設定されていることを確認します
* "_MRTK チュートリアル_" など、適切な **[Project Name]\(プロジェクト名\)** を入力します
* プロジェクトを格納するための適切な **[Location]\(場所\)** を選択します。たとえば、_D:\MixedRealityLearning_ など
* **[Create]\(作成\)** ボタンをクリックして、新しい Unity プロジェクトを作成して起動します

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> Windows で作業している場合は、255 文字の MAX_PATH 制限があります。 Unity はこれらの制限の影響を受け、255 文字を超えるファイル パスが存在する場合、コンパイルに失敗する可能性があります。 そのため、できるだけドライブのルートの近くに Unity プロジェクトを保存することを強くお勧めします。

Unity によってプロジェクトが作成されるまで待ちます。

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality 用に Unity プロジェクトを構成する

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

このセクションでは、ビルド プラットフォームの切り替え、仮想現実の有効化、および空間認知の有効化を行います。

### <a name="1-switch-build-platform"></a>1.ビルド プラットフォームの切り替え

Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** を選択し、[Build Settings]\(ビルド設定\) ウィンドウを開きます。

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

[Build Settings]\(ビルド設定\) ウィンドウで、 **[Universal Windows Platform]\(ユニバーサル Windows プラットフォーム\)** を選択して、 **[Switch Platform]\(プラットフォームの切り替え\)** ボタンをクリックします。

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

Unity がプラットフォームの切り替えを完了するまで待ちます。

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

Unity でプラットフォームの切り替えが完了したら、赤色の **x** アイコンをクリックして、[Build Settings]\(ビルド設定\) ウィンドウを閉じます。

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a>2.仮想現実を有効にする

> [!NOTE]
> 仮想現実を有効にすることは、立体視 (それぞれの目で異なる画像をレンダリングする) を有効にすることを指すため、複合現実および拡張現実ヘッドセットにも適用されます。

Unity メニューで、 **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクト設定...\)** を選択し、[Project Settings]\(プロジェクト設定\) ウィンドウを開きます。

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレイヤー\)**  >  **[XR Settings]\(XR 設定\)** を選択して、XR の設定を展開します。

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

[XR Settings]\(XR 設定\) で、 **[Virtual Reality Supported]\(仮想現実がサポートされている\)** チェックボックスをオンにして、仮想現実を有効にします。次に、 **+** アイコンをクリックし、 **[Windows Mixed Reality]** を選択して Windows Mixed Reality SDK を追加します。

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

Unity が SDK の追加を完了するまで待ちます。

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

Unity で SDK の追加が完了したら、次のように XR の設定を最適化します。

* Windows Mixed Reality の **[Depth Format]\(深度形式\)** を **[16-bit depth]\(16 ビット深度\)** に設定します
* Windows Mixed Reality の **[Enable Depth Sharing]\( 深度の共有を有効にする\)** チェックボックスをオンにします
* **[Stereo Rendering Mode]\(ステレオ レンダリング モード\)\*** を **[Single Pass Instanced]\(シングル パス インスタンス\)** に設定します

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> Unity を Windows Mixed Reality 向けに最適化する方法の詳細については、「[Unity の推奨設定](recommended-settings-for-unity.md)」ドキュメントを参照してください。

### <a name="3-enable-spatial-perception"></a>3.空間認知を有効にする

> [!NOTE]
> 空間認知を使用すると、Windows Mixed Reality デバイス上で空間マッピングのメッシュを視覚化できます。

[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレイヤー\)**  >  **[Publishing Settings]\(公開設定\)** を選択して、公開の設定を展開します。

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

[Publishing Settings]\(公開設定\)で、 **[Capabilities]\(機能\)** セクションまで下にスクロールし、 **[SpatialPerception]** チェックボックスをオンにします。

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

[Project Settings]\(プロジェクト設定\) ウィンドウを閉じます。

## <a name="import-textmesh-pro-essential-resources"></a>TextMesh Pro の重要なリソースをインポートする

> [!NOTE]
> このパッケージは、Mixed Reality Toolkit の UI 要素で必要とされるためインポートします。

Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[TextMeshPro]**  >  **[Import TMP Essential Resources]\(TMP の重要なリソースをインポート\)** を選択します。

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a>Mixed Reality ツールキットをインポートする

Unity カスタム パッケージをダウンロードします。

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

Unity メニューで、 **[Assets]\(アセット\)**  >  **[Import Package]\(パッケージのインポート\)**  >  **[Custom Package...]\(カスタム パッケージ...\)** を選択して [Import package...]\(パッケージのインポート...\) ウィンドウを開きます。

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

[Import package...]\(パッケージのインポート...\) ウィンドウで、ダウンロードした **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** を選択し、 **[Open]\(開く\)** ボタンをクリックします。

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a>Mixed Reality ツールキット用に Unity プロジェクトを構成する

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

パッケージがインポートされると、[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが表示されます。 表示されていない場合は、Unity メニューの **[Mixed Reality Toolkit]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** を選択して開きます。

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウで、 **[Modify Configurations]\(構成の変更\)** セクションを展開し、 **[Enable MSBuild for Unity]\(MSBuild for Unity を有効にする\)** チェックボックスを<u>オフ</u>にし、他のすべてのオプションがオンになっていることを確認し、 **[Apply]\(適用\)** ボタンをクリックして設定を適用します。

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> MSBuild for Unity は使用するすべての SDK をサポートしていない場合があり、有効にした後は無効にするのが困難な場合があります。 そのため、MSBuild for Unity を有効にしないことを強くお勧めします。

## <a name="configure-the-mixed-reality-toolkit"></a>Mixed Reality ツールキットを構成する
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

Unity メニューで、 **[Mixed Reality Toolkit]\(Mixed Reality ツールキット\)**  >  **[Add to Scene and Configure...]\(シーンに追加して構成する...\)** の順に選択して、Mixed Reality ツールキットを現在のシーンに追加します。

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

[Hierarchy]\(階層\) ウィンドウで MixedRealityToolkit オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、Mixed Reality ツールキットの構成プロファイルが **DefaultMixedRealityToolkitConfigurationProfile** に設定されていることを確認します。

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

> [!IMPORTANT]
> 通常、HoloLens 2 の開発時には DefaultHoloLens2ConfigurationProfile を使用します。 ただし、このチュートリアルでは、DefaultMixedRealityToolkitConfigurationProfile を使用します。次のチュートリアル「[ユーザー インターフェイスの作成と Mixed Reality ツールキットの構成](mrlearning-base-ch2.md)」で、DefaultHoloLens2ConfigurationProfile に変更します。

Unity メニューで、 **[File]\(ファイル\)**  >  **[Save As...]\(名前を付けて保存...\)** を選択して [Save Scene]\(シーンの保存\) ウィンドウを開きます。

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

[Save Scene]\(シーンの保存\) ウィンドウで、プロジェクトの **[Scenes]\(シーン\)** フォルダーに移動し、シーンに適切な名前を付け (たとえば、_GettingStarted_)、 **[Save]\(保存\)** ボタンをクリックしてシーンを保存します。

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a>デバイスへのアプリケーションのビルド

### <a name="1-build-the-unity-project"></a>1.Unity プロジェクトのビルド

Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** を選択し、[Build Settings]\(ビルド設定\) ウィンドウを開きます。

[Build Settings]\(ビルド設定\) ウィンドウで、 **[Add Open Scenes]\(開いているシーンを追加する\)** ボタンをクリックして、 **[Scenes In Build]\(ビルド内のシーン\)** リストの現在のシーンを追加します。次に **[Build]\(ビルド\)** ボタンをクリックして、[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウを開きます。

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウで、ビルドを格納する適切な場所 (たとえば _D:\MixedRealityLearning\Builds_) を選択し、新しいフォルダーを作成して適切な名前 (たとえば _GettingStarted_) を付け、 **[Select Folder]\(フォルダーの選択\)** ボタンをクリックしてビルド処理を開始します。

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

Unity がビルド処理を完了するまで待ちます。

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2.アプリのビルドと配置

ビルド処理が完了すると、Unity は、ビルドを格納した場所を開くように Windows ファイル エクスプローラーを表示します。 フォルダー内を移動し、ソリューション ファイルをダブルクリックして Visual Studio で開きます。

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、[「ツールのインストール」](install-the-tools.md)ドキュメントで示されている、前提条件となるすべてのコンポーネントがインストールされていることを確認してください

**[マスター]** または **[リリース]** 構成、 **[ARM]** アーキテクチャ、ターゲットとして **[デバイス]** を選択して、HoloLens 2 用に Visual Studio を構成します。

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

> [!NOTE]
> オプションとして [デバイス] が表示されない場合は、既定のスタートアップ プロジェクトを IC2Lpp プロジェクトから UWP プロジェクトに変更することが必要な場合があります。 **ソリューション エクスプローラー**で、 **[yourprojectname (Universal Windows)]\(yourprojectname (ユニバーサル Windows)\)** を右クリックし、 **[スタートアップ プロジェクトに設定]** を選択します。 

HoloLens 2 をコンピューターに接続します。

> [!IMPORTANT]
> デバイスに対してビルドする前に、デバイスが開発者モードになっており、かつ、開発コンピューターとペアリングされている必要があります。 この両方のステップを完了するには、[こちらの手順](using-visual-studio.md)に従います。

最後の手順として、 **[デバッグ]**  >  **[デバッグなしで開始]** を選択してビルドし、デバイスにデプロイします。

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

これらの手順では、HoloLens 2 デバイスに配置することを前提としていますが、[HoloLens 2 エミュレーター](using-the-hololens-emulator.md)に配置することも、[サイドローディング用のアプリ パッケージ](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)を作成することもできます。

[デバッグなしで開始] を選択すると、ビルドが成功した時点でアプリケーションがデバイス上ですぐに起動しますが、デバッガーがアタッチされていない状態であり、Visual Studio にデバッグ情報は表示されません。 これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。

アプリケーションを自動的に起動せずにデバイスに配置するには、[ビルド] > [ソリューションの配置] を選択します。

## <a name="congratulations"></a>結論

<!-- TODO: Consider cleanup and adding in app screenshots -->
これで、最初の HoloLens 2 アプリケーションがデプロイされました。 手順に従うと、HoloLens 2 によって認識されたすべてのサーフェイスに対応する空間マッピングのメッシュが表示されるはずです。 さらに、ハンド トラッキング用の手および指に対するインジケーターと、アプリケーションのパフォーマンスを監視するためのフレーム レート カウンターも表示されるはずです。 これらは、Mixed Reality ツールキットに含まれている、すぐに使用できる基礎となる部分のほんの一部です。 以降のチュートリアルでは、HoloLens 2 と Mixed Reality ツールキットの機能を十分に探索できるように、シーンにコンテンツや対話機能を追加する作業を開始します。

> [!NOTE]
> アプリでは、診断プロファイラーが表示される場合があります。この表示を切り替えるには、音声コマンド **Toggle Diagnostics** を使用します。 ただし、一般に、アプリに対する変更がパフォーマンスに影響を与える可能性がある場合を把握するために、開発中に常にプロファイラーを表示したままにしておくことをお勧めします。たとえば、HoloLens 2 アプリケーションは [60 FPSで継続的に実行](understanding-performance-for-mixed-reality.md)される必要があります。

[次のチュートリアル:3.ユーザー インターフェイスの作成と Mixed Reality ツールキットの構成](mrlearning-base-ch2.md)
