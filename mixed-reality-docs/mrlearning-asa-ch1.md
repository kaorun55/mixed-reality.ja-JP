---
title: Azure 空間アンカーチュートリアル-1. Azure 空間アンカーの概要
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 21883e95e92f8808bcf270e6d8091f31933ab6fa
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250867"
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

## <a name="prerequisites"></a>前提条件

>[!TIP]
>[概要チュートリアル](mrlearning-base.md)シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。

* 適切な[ツールがインストール](install-the-tools.md)されている WINDOWS 10 PC
* Windows 10 SDK 10.0.18362.0 以降
* 基本的なC#プログラミング機能
* [開発用に構成され](using-visual-studio.md#enabling-developer-mode)た HoloLens 2 デバイス
* Unity 2019.2 がインストールされ、ユニバーサル Windows プラットフォームビルドサポートモジュールが追加された<a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity ハブ</a>
* 「[クイックスタート: Azure 空間アンカーを使用した Unity HoloLens アプリの作成](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)」チュートリアルの「[空間アンカーリソースの作成](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクションを完了します。

> [!IMPORTANT]
> このチュートリアルシリーズで推奨されている Unity バージョンは Unity 2019.2 です。 これは、前にリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。

## <a name="creating-the-unity-project"></a>Unity プロジェクトの作成
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発の準備をします。 そのためには、「[プロジェクトと最初のアプリケーションの初期化](mrlearning-base-ch1.md)」に従ってください。これには、次の手順が含まれています。[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)の手順は除きます。

1. [新しい Unity プロジェクトを作成](mrlearning-base-ch1.md#create-new-unity-project)し、適切な名前 ( *Mrtk チュートリアル*など) を指定します。

2. [Windows Mixed Reality 用に Unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [TextMesh Pro の重要なリソースをインポートする](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Mixed Reality Toolkit をインポートする](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Mixed Reality Toolkit 用に Unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Unity シーンに Mixed Reality Toolkit を追加](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)し、シーンに適切な名前を付けます (たとえば、 *AzureSpatialAnchors* )。

> [!CAUTION]
> 前述のように、「 [Mixed Reality Toolkit の unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)」の手順で説明したように、MSBuild for unity は使用するすべての sdk をサポートしていない場合があり、有効にした後に無効にするのは困難な場合があります。 そのため、Unity で MSBuild を有効にしないことを強くお勧めします。

## <a name="adding-inbuilt-unity-packages"></a>組み込み Unity パッケージの追加
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

このセクションでは、Unity の組み込みの AR パッケージをインストールします。これは、次のセクションでインポートする Azure 空間アンカー SDK で必要とされるためです。

Unity メニューで、[ **Window** > **Package Manager**] を選択します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> この一覧には、AR Foundation パッケージが表示されるまでに数秒かかることがあります。

パッケージマネージャー ウィンドウで、 **AR Foundation** を選択し、**インストール** ボタンをクリックしてパッケージをインストールします。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>チュートリアル資産のインポート

次の Unity カスタムパッケージをダウンロードし**て、一覧に記載さ**れている順序で**インポート**します。

* [AzureSpatialAnchors unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (バージョン 2.1.1)
* [MRTK。HoloLens2. 2.2.0.1. unitypackage を実行します。](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.1.unitypackage)
* [MRTK。HoloLens2. AzureSpatialAnchors. 2.2.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.2.0.0.unitypackage)

> [!TIP]
> Unity カスタムパッケージをインポートする方法については、「 [Mixed Reality Toolkit のインポート](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」の手順を参照してください。

チュートリアルのアセットをインポートすると、プロジェクトウィンドウは次のようになります。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>シーンの作成と準備
<!-- TODO: Consider renaming to 'Preparing the scene' -->

このセクションでは、チュートリアル prefabs の一部を追加してシーンを準備します。

[プロジェクト] ウィンドウで、[**アセット** > **mrtk] に移動します。AzureSpatialAnchors** > **Prefabs**フォルダー。 CTRL ボタンを押したまま、 **Buttonparent**、 **debugwindow**、**命令**、および**parentanchor**をクリックして、4つの prefabs を選択します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

4つの prefabs を選択したまま、[階層] ウィンドウにドラッグしてシーンに追加します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

シーン内のオブジェクトに焦点を当てるには、ParentAnchor オブジェクトをダブルクリックして、もう一度もう一度ズームします。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> シーンに大きいアイコンが見られる場合 (たとえば、大きなフレーム \ ' アイコンが煩雑である場合)、ギズモを off の位置に<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">切り替える</a>ことによって、これらを非表示にすることができます。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>シーンを操作するためのボタンの構成

このセクションでは、スクリプトをシーンに追加して、アプリケーションでローカルアンカーと Azure 空間アンカーの両方が動作する方法の基礎を示す一連のボタンイベントを作成します。

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1. Pressable Button Holo レンズ 2 (Script) コンポーネントを構成します。

[階層] ウィンドウで、 **Buttonparent**オブジェクトを展開し、 **StartAzureSession**という名前の最初の子オブジェクトを選択します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

[インスペクター] ウィンドウで、 **Pressable Button Holo レンズ 2 (Script)** コンポーネントを見つけて、[ **+** ] アイコンをクリックして、ボタンが押された **()** イベントに新しいイベントリスナーを追加します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

[階層] ウィンドウで StartAzureSession オブジェクトを選択した状態で、[階層] ウィンドウから**Parentanchor**オブジェクトをクリックして、追加したイベントリスナーの空の **[None (オブジェクト)** ] フィールドに移動します。このボタンをクリックすると、parentanchor オブジェクトがボタンの押されたイベントをリッスンするようになります。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

同じイベントリスナーの **[関数なし]** ドロップダウンをクリックし、[ **AnchorModuleScript** > **StartAzureSession ()** ] を選択して、このボタンからボタンを押したイベントが発生したときにトリガーされるアクションとして StartAzureSession () 関数を設定します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2. 対話型 (スクリプト) コンポーネントを構成します。

[階層] ウィンドウで StartAzureSession オブジェクトを選択した状態で、[インスペクター] ウィンドウで**対話型 (スクリプト)** コンポーネントを見つけ、 **[OnClick ()]** イベントについて上記の手順1と同じプロセスを繰り返します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3. 残りのボタンを構成する

残りの各ボタンについて、上記の手順 1. と 2. で説明したプロセスを完了して、 **Button 押された ()** イベントと**OnClick ()** イベントの両方に関数を割り当てます。

* **Stopazuresession**オブジェクトの場合は、AnchorModuleScript > **stopazuresession ()** 関数を割り当てます。
* **Createazureanchor**オブジェクトの場合は、AnchorModuleScript > **createazureanchor ()** 関数を割り当てます。
  * 次に、 **Parentanchor**を [空の**なし (ゲームオブジェクト)** ] フィールドにもう一度ドラッグします。
* **Removelocalanchor**オブジェクトの場合は、AnchorModuleScript > **removelocalanchor ()** 関数を割り当てます。
  * 次に、 **Parentanchor**を [空の**なし (ゲームオブジェクト)** ] フィールドにもう一度ドラッグします。
* **Findazureanchor**オブジェクトの場合は、AnchorModuleScript > **findazureanchor ()** 関数を割り当てます。
* **Deleteazureanchor**オブジェクトの場合は、AnchorModuleScript > **deleteazureanchor ()** 関数を割り当てます。

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4. シーンを Azure リソースに接続する

階層 ウィンドウで**parentanchor**オブジェクトを選択し、インスペクター ウィンドウで **空間アンカーマネージャー (スクリプト)** コンポーネントまでスクロールします。

次に、 **[資格情報]** セクションで、このチュートリアルの[前提条件](mrlearning-asa-ch1.md#prerequisites)の一部として作成した空間アンカーアカウント id とキーを、対応する**空間アンカーアカウント Id**と**空間アンカーアカウントキー**フィールドに貼り付けます。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Azure 空間アンカーの基本的な動作を試す

これで、Azure 空間アンカーの基本を示すようにシーンが構成されたので、Azure 空間アンカーじを体験できるようにアプリをデプロイします。

### <a name="1-add-additional-required-capabilities"></a>1. その他の必要な機能を追加する

[Unity] メニューの [**プロジェクト設定**の > **編集**] を選択して、[プレーヤーの設定] ウィンドウを開きます。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

プレーヤーの設定 ウィンドウで、**プレーヤー**、**発行の設定** の順に選択します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

発行の**設定**で、 **[機能]** セクションまで下にスクロールし、チュートリアルの冒頭でプロジェクトを作成したときに有効にした**Internetclient**、**マイク**、 **SpatialPerception**の機能が有効になっていることを再度確認します。 次に、 **Internetclientserver**、 **PrivateNetworkClientServer**、 **Removablestorage**、および**web カメラ**の機能を有効にします。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. アプリを HoloLens 2 にデプロイする

Azure 空間アンカーは Unity では実行できません。そのため、Azure 空間アンカー機能をテストするには、プロジェクトをデバイスにデプロイする必要があります。

> [!TIP]
> HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法に関する注意事項については、「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」の指示を参照してください。

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. アプリを HoloLens 2 で実行し、アプリ内の指示に従います。

> [!CAUTION]
> Azure 空間アンカーは、インターネットを使用してアンカーデータを保存して読み込みます。そのため、デバイスがインターネットに接続されていることを確認してください。

アプリケーションがデバイスで実行されている場合は、Azure 空間アンカーチュートリアルの手順パネルに表示される画面の指示に従います。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>エクスペリエンスを固定する

前のセクションでは、Azure 空間アンカーの基礎について学習しました。 キューブを使用して、アタッチされたアンカーで親ゲームオブジェクトを表現し、視覚化しています。 このセクションでは、ParentAnchor オブジェクトの子として配置することで、エクスペリエンス全体を固定する方法について説明します。

### <a name="1-add-the-rocket-launcher-experience"></a>1. ロケットランチャーエクスペリエンスを追加する

プロジェクト ウィンドウで、**アセット** >  **mrtk に移動します。チュートリアル: GettingStarted** **Prefabs** > **RocketLauncher**フォルダーで、 **RocketLauncher_Complete** prefab を選択します。 > 

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

RocketLauncher_Complete prefab を選択したまま、[階層] ウィンドウの**Parentanchor**オブジェクトの上にドラッグして、parentanchor オブジェクトの子にします。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2. ロケットランチャーエクスペリエンスの位置を変更する

次の例のように、 **RocketLauncher_Complete**オブジェクトを適切なスケールと方向に配置、回転、拡大縮小します。また、 **parentanchor**オブジェクトが引き続き公開されていることも確認します。

* 変換**位置**X = 1、Y = 0、Z = 3.75
* 変換の**回転**X = 0、Y = 90、Z = 0
* 変換**スケール**X = 10、Y = 10、Z = 10

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

アプリケーションでは、ユーザーがキューブを移動して、ロケットランチャーエクスペリエンス全体を再配置できるようになりました。

> [!TIP]
> 再配置オブジェクト (このチュートリアルで使用されるキューブなど) の使用、エクスペリエンスを示すボタンの使用、画面の位置と回転の使用など、さまざまな操作を行うためのさまざまなユーザーエクスペリエンスフローがあります。ギズモなど。

## <a name="congratulations"></a>結論

このチュートリアルでは、Azure 空間アンカーの基礎について学習しました。 このチュートリアルでは、Azure 空間アンカーセッションを開始および停止するために必要なさまざまな手順を説明し、1つのデバイスで Azure 空間アンカーを作成、アップロード、およびダウンロードするためのいくつかのボタンを紹介しました。

次のレッスンでは、アプリケーションを再起動した後でも、Azure anchor Id を HoloLens 2 に保存し、複数のデバイス間でアンカー Id を転送して空間アラインメントを実現する方法について説明します。

[次のレッスン: 2. Azure 空間アンカーの保存、取得、共有](mrlearning-asa-ch2.md)
