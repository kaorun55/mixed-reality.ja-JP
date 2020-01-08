---
title: Azure 空間アンカーチュートリアル-1. Azure 空間アンカーの概要
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, チュートリアル, hololens
ms.openlocfilehash: e62d3626ec6f2dbf8b66378212afab7db2f56422
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334449"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Azure 空間アンカーの概要

## <a name="overview"></a>概要

2番目のシリーズの HoloLens 2 チュートリアルへようこそ。 この3部構成のチュートリアルシリーズでは、Azure 空間アンカーの基礎について説明します。

この最初のチュートリアル「 [Azure 空間アンカーの概要](mrlearning-asa-ch1.md)」では、azure セッションを開始および停止し、1つのデバイスで azure アンカーを作成、アップロード、およびダウンロードするために必要なさまざまな手順について説明します。

2番目のチュートリアル「 [Azure 空間アンカーの保存、取得、および共有](mrlearning-asa-ch2.md)」では、複数のアプリセッションにわたって Azure 空間アンカーを保存する方法について説明します。これは、HoloLens 2 のストレージにアンカー情報を保存し、このアンカー情報を複数デバイスのアンカーの配置用に他のデバイスに共有する方法を説明します。

3番目のチュートリアル「 [Azure 空間アンカーフィードバックの表示](mrlearning-asa-ch3.md)」では、azure 空間アンカーを使用する場合のアンカーイベントと状態に関するフィードバックをユーザーに提供する方法について説明します。

## <a name="objectives"></a>目標

* HoloLens 2 用の Azure 空間アンカーを使用した開発の基礎について説明します。
* 空間アンカーを作成、アップロード、ダウンロードする

## <a name="prerequisites"></a>必要条件

>[!TIP]
>[概要チュートリアル](mrlearning-base.md)シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。

* 適切な[ツールがインストール](install-the-tools.md)されている WINDOWS 10 PC
* Windows 10 SDK 10.0.18362.0 以降
* 基本的なC#プログラミング機能
* [開発用に構成され](using-visual-studio.md#enabling-developer-mode)た HoloLens 2 デバイス
* 「[クイックスタート: Azure 空間アンカーを使用した Unity HoloLens アプリの作成](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)」チュートリアルの「[空間アンカーリソースの作成](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクションを完了します。

>[!IMPORTANT]
>このチュートリアルシリーズでは<a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019.1</a>が必要であり、推奨されるバージョンは unity 2019.1.14 です。 これは、前にリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。

## <a name="creating-the-unity-project"></a>Unity プロジェクトの作成

このセクションでは、新しい Unity プロジェクトを作成し、Windows Mixed Reality 用に構成します。

1. Unity プロジェクトを作成し、 _Azure 空間アンカーチュートリアル_などの適切な名前を付けます。

2. Windows Mixed Reality の Unity プロジェクトを構成します。

    >[!TIP]
    >Unity プロジェクトを作成し、Windows Mixed Reality 用に構成する方法について[は、「](mrlearning-base-ch1.md#create-new-unity-project)プロジェクトの初期化」と「最初のアプリケーションのチュートリアル[」シリーズの](mrlearning-base.md)「プロジェクトの初期化」と「[最初のアプリケーション](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1)の[構成](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)」のセクションを参照してください。

## <a name="adding-inbuilt-unity-packages"></a>組み込み Unity パッケージの追加

このセクションでは、プロジェクトで使用するツールキットと Sdk に必要な組み込みの Unity アセットとパッケージを追加します。

1. TMP の重要なリソースをインポートします。

    >[!NOTE]
    >このパッケージは、Mixed Reality Toolkit によって要求されているため、追加しています。

    Unity メニューで、[ **Window** > **TextMeshPro** ] を選択し > **TMP 必須リソースをインポート**します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.1.png)

    Unity パッケージのインポート ポップアップウィンドウで、まず **すべて** をクリックしてすべてのアセットを選択し、**インポート** ボタンをクリックしてアセットをインポートします。

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.2.png)

2. AR Foundation をインストールします。

    >[!NOTE]
    >このパッケージは Azure 空間アンカー SDK で必要とされるため、追加しています。

    Unity メニューで、[**ウィンドウ** > **パッケージマネージャー**] を選択します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.1.png)

    パッケージマネージャー ウィンドウで、 **AR Foundation** を選択し、**インストール** ボタンをクリックしてパッケージをインストールします。

    >[!IMPORTANT]
    >この一覧には、AR Foundation パッケージが表示されるまでに数秒かかることがあります。

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a>チュートリアル資産のインポート

このセクションでは、すべてのチュートリアル資産をダウンロードしてインポートします。

1. アセットをダウンロードします。

    * [AzureSpatialAnchors unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (バージョン 2.0.0)
    * [MixedReality. 2.1.0. unitypackage のようになります。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [MRTK。HoloLens2. 2.1.0.1. unitypackage を実行します。](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [MRTK。HoloLens2. AzureSpatialAnchors. 2.1.0.1. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. アセットをインポートします。

    Unity メニューで、[ **Assets** > **Import Package** > **カスタムパッケージ**] を選択します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.1.png)

    Import package... (パッケージのインポート)...ポップアップウィンドウで、 **AzureSpatialAnchors unitypackage**を選択し、**開く** ボタンをクリックします。

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.2.png)

    Unity パッケージのインポート ポップアップウィンドウで、まず **すべて** をクリックしてすべてのアセットを選択し、**インポート** ボタンをクリックしてアセットをインポートします。

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.3.png)

    残りのアセットパッケージをインポートするには、この手順を繰り返します。 完了すると、Unity プロジェクトの**Assets**フォルダーにこれらのサブフォルダーが含まれます。

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a>シーンの作成と準備

このセクションでは、Mixed Reality Toolkit といくつかのチュートリアル prefabs を追加して、シーンの作成と準備を行います。

1. 新しいシーンを作成します。

    Unity メニューで、[**ファイル** > **新しいシーン**] を選択します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.1.png)

    Unity メニューで、[**ファイル** > **名前を付けて保存...** ] を選択します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.2.png)

    シーンの保存 ポップアップウィンドウで、プロジェクトの **シーン** フォルダーに移動し、シーンに適切な名前 ( _ASATutorialScene_など) を付けて、**保存** ボタンをクリックしてシーンを保存します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    >シーンは、プロジェクトの Assets フォルダー内にある限り、任意の場所に保存できます。 ただし、プロジェクトを整理し続けるには、通常、プロジェクトの [シーン] フォルダーに保存することをお勧めします。

2. Mixed Reality Toolkit を追加します。

    Unity メニューで、 **[Mixed Reality Toolkit]** を選択し > [**シーンに追加] と [構成...** ] を選択します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.1.png)

    [Select MixedRealityToolkitConfigurationProfile] ポップアップウィンドウで、 **DefaultHoloLens2ConfigurationProfile**をクリックして、シーンの MRTK 構成プロファイルとして設定します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.2.png)

    Unity メニューで、[**ファイル** > **保存**] を選択してシーンを保存します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    >このチュートリアルで作業するときに、キーボードショートカットの CTRL + S (macOS のコマンド + S) を使用して、シーンをすばやく保存できます。

3. チュートリアル prefabs を追加します。

    [プロジェクト] パネルで、[**アセット** > **mrtk] に移動します。AzureSpatialAnchors** > **Prefabs**フォルダー。 CTRL ボタンを押したまま (macOS の場合はコマンド)、 **[Buttonparent]** 、 **[debugwindow]** 、および **[parentanchor]** をクリックして、3つの prefabs を選択します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.1.png)

    3つの prefabs を選択したまま、[階層] パネルにドラッグしてシーンに追加します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.2.png)

    シーン内のオブジェクトに焦点を当てるには、ParentAnchor オブジェクトをダブルクリックして、もう一度もう一度ズームします。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    >シーンに大きいアイコンが見られる場合 (たとえば、大きなフレーム \ ' アイコンが煩雑である場合)、ギズモを off の位置に<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">切り替える</a>ことによって、これらを非表示にすることができます。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>シーンを操作するためのボタンの構成

このセクションでは、prefabs とスクリプトをシーンに追加して、アプリケーションでローカルアンカーと Azure 空間アンカーの両方が動作する方法の基礎を示す一連のボタンを作成します。

1. Pressable Button Holo レンズ 2 (スクリプト) コンポーネントを構成します。

    [階層] パネルで、 **Buttonparent**オブジェクトを展開し、 **StartAzureSession**という名前の最初の子オブジェクトを選択します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.1.png)

    [インスペクター] パネルで、[ **Pressable] ボタン Holo レンズ 2 (script)** コンポーネントまで下にスクロールし、[ **+** ] アイコンをクリックして、**ボタン押下 ()** イベントに新しいイベントリスナーを追加します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.2.png)

    階層 パネルで StartAzureSession オブジェクトを選択した状態で、階層 パネルから**Parentanchor**オブジェクトをクリックして、追加したイベントリスナーの空の**なし (オブジェクト)**  フィールドに移動します。これにより、このボタンからボタンの押されたイベントを、parentanchor オブジェクトがリッスンするようになります。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.3.png)

    同じイベントリスナーの **[関数なし]** ドロップダウンをクリックし、[ **AnchorModuleScript** > **StartAzureSession ()** ] を選択して、このボタンからボタンを押したイベントが発生したときにトリガーされるアクションとして StartAzureSession () 関数を設定します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.4.png)

2. 対話型 (スクリプト) コンポーネントを構成します。

    階層 パネルで StartAzureSession オブジェクトを選択した状態で、インスペクター パネルの **対話型 (スクリプト)** コンポーネントまで下にスクロールし、**OnClick ()** イベントに対して上記の手順1と同じ手順を繰り返します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-2.1.png)

3. 残りのボタンを構成する

    残りの各ボタンについて、上記の手順 1. と 2. で説明したプロセスを完了して、次のボタンが押された () イベントと OnClick () イベントの両方に関数を割り当てます。

    * **Stopazuresession**オブジェクトの場合は、 **stopazuresession ()** 関数を割り当てます。
    * **Createanchor**オブジェクトの場合は、 **createazureanchor ()** 関数を割り当ててから、 **Parentanchor**を [空の**なし (ゲームオブジェクト)** ] フィールドにもう一度ドラッグします。
    * アンカーオブジェクト**の検索を開始**するには、 **findazureanchor ()** 関数を割り当てます。
    * **Delete Azure anchor**オブジェクトの場合は、 **deleteazureanchor ()** 関数を割り当てます。
    * **Delete Local anchor**オブジェクトの場合は、 **removelocalanchor ()** 関数を割り当ててから、 **Parentanchor**を [空の**なし (ゲームオブジェクト)** ] フィールドにもう一度ドラッグします。

4. シーンを Azure リソースに接続する

    階層 パネルで**parentanchor**オブジェクトを選択し、インスペクター パネルで **空間アンカーマネージャー (スクリプト)** コンポーネントまでスクロールします。

    次に、 **[資格情報]** セクションで、空間アンカーアカウント Id とキーを、対応する**空間アンカーアカウント Id**と**空間アンカーアカウントキー**フィールドに貼り付けます。

    >[!NOTE]
    >このチュートリアルの[前提条件](mrlearning-asa-ch1.md#prerequisites)の一部として、空間アンカーアカウント Id とキーを作成しました。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    >シーンを保存していることを確認します。

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Azure 空間アンカーの基本的な動作を試す

これで、Azure 空間アンカーの基本を示すようにシーンが構成されたので、Azure 空間アンカーじを体験できるようにアプリをデプロイします。

1. 必要な機能を追加します。

    [Unity] メニューの [**プロジェクト設定**の > **編集**] を選択して、[プレーヤーの設定] パネルを開きます。

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.1.png)

    プレーヤーの 設定 パネルで、**プレーヤー**、**設定の発行** の順に選択します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.2.png)

    **[発行の設定]** で、 **[機能]** セクションまで下にスクロールし、チュートリアルの最初にプロジェクトを作成したときに有効にした**SpatialPerception**が有効になっていることを再度確認します。 次に、 **Internetclient**、 **internetclientserver**、 **PrivateNetworkClientServer**、 **Removablestorage**、 **Webcam**、および**マイク**機能が有効になります。

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.3.png)

2. アプリを HoloLens 2 にデプロイします。

    >[!TIP]
    >HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、「[入門チュートリアル](mrlearning-base.md)」シリーズの一部である「[プロジェクトの初期化」および「最初のアプリケーション](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1)のチュートリアル」の「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」セクションを参照してください。

3. アプリを実行し、アプリ内の指示に従います。

    >[!CAUTION]
    >Azure 空間アンカーは、インターネットを使用してアンカーデータを保存して読み込みます。そのため、デバイスがインターネットに接続されていることを確認してください。

    アプリケーションがデバイスで実行されている場合は、 **Azure 空間アンカーモジュール**の [命令] パネルに表示される画面の指示に従います。

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a>エクスペリエンスを固定する

前のセクションでは、Azure 空間アンカーの基礎について学習しました。 キューブを使用して、アタッチされたアンカーで親ゲームオブジェクトを表現し、視覚化しています。 このセクションでは、ParentAnchor オブジェクトの子として配置することで、エクスペリエンス全体を固定する方法について説明します。

1. ロケットランチャーエクスペリエンスを追加します。

    [プロジェクト] パネルで、[**アセット** > **mrtk] に移動します。チュートリアル。 GettingStarted** **Prefabs**フォルダーを起動し、**ロケット Launcher_Complete** prefab を選択します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.1.png)

    ロケット Launcher_Complete prefab を選択したまま、[階層] パネルの**Parentanchor**オブジェクトの上にドラッグして、parentanchor オブジェクトの子にします。

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.2.png)

2. ロケットランチャーエクスペリエンスの位置を変更します。

    **Parentanchor** (キューブ) が引き続き公開されるように、モジュールの**ロケット Launcher_Complete**オブジェクトを移動します。

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-2.1.png)

    アプリケーションでは、ユーザーがキューブを移動して、ロケットランチャーエクスペリエンス全体を再配置できるようになりました。

    >[!TIP]
    >再配置オブジェクト (このチュートリアルで使用されるキューブなど) の使用、エクスペリエンスを示すボタンの使用、画面の位置と回転の使用など、さまざまな操作を行うためのさまざまなユーザーエクスペリエンスフローがあります。ギズモなど。

## <a name="congratulations"></a>結論

このチュートリアルでは、Azure 空間アンカーの基礎について学習しました。 このレッスンでは、Azure セッションを開始および停止するために必要なさまざまな手順を説明し、1つのデバイスに azure のアンカーを作成、アップロード、ダウンロードするためのボタンをいくつか紹介しました。

次のレッスンでは、アプリケーションを再起動した後でも、Azure anchor Id を HoloLens 2 に保存し、複数のデバイス間でアンカー Id を転送して空間アラインメントを実現する方法について説明します。

[次のレッスン: 2. Azure 空間アンカーの保存、取得、共有](mrlearning-asa-ch2.md)
