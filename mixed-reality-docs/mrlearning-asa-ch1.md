---
title: Azure Spatial Anchors チュートリアル - 1. Azure Spatial Anchors をお使いになる前に
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 47063fbf9a1b9f3a43497a0742deba2c16b53d99
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362062"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1.Azure Spatial Anchors をお使いになる前に

## <a name="overview"></a>概要

HoloLens 2 チュートリアルのシリーズ 2 へようこそ。 この 3 部構成のチュートリアル シリーズでは、Azure Spatial Anchors の基礎について学習します。

この最初のチュートリアル「[Azure Spatial Anchors をお使いになる前に](mrlearning-asa-ch1.md)」では、Azure セッションの開始と停止、単一のデバイス上での Azure アンカーの作成、アップロード、ダウンロードに必要なさまざまな手順を学習します。

2 番目のチュートリアル「[Azure Spatial Anchors の保存、取得、および共有](mrlearning-asa-ch2.md)」では、HoloLens 2 のストレージにアンカー情報を保存することで、複数のアプリ セッションにわたって Azure Spatial Anchors を保存する方法と、このアンカー情報を他のデバイスと共有して複数のデバイスのアンカー位置合わせを行う方法について学習します。

3 番目のチュートリアル「[Azure Spatial Anchors フィードバックの表示](mrlearning-asa-ch3.md)」では、Azure Spatial Anchors を使用する際のアンカーのイベントと状態に関するフィードバックをユーザーに提供する方法について学習します。

## <a name="objectives"></a>目標

* HoloLens 2 用の Azure Spatial Anchors を使用した開発の基礎について学習する
* 空間アンカーを作成、アップロード、ダウンロードする

## <a name="prerequisites"></a>前提条件

>[!TIP]
>[入門チュートリアル](mrlearning-base.md) シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。

* 正しい[ツールがインストールされている](install-the-tools.md)構成済みの Windows 10 PC
* Windows 10 SDK 10.0.18362.0 以降
* 基本的な C# プログラミング能力
* [開発用に構成された](using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス
* Unity 2019.2.X がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>
* 「[Spatial Anchors リソースを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクション ([クイック スタート:Azure Spatial Anchors を使用する Unity HoloLens アプリを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) チュートリアルにあります) を完了します。

> [!IMPORTANT]
> このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.2.X です。 これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。

## <a name="creating-the-unity-project"></a>Unity プロジェクトの作成
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備します。

このためには、まず「[プロジェクトと最初のアプリケーションの初期化](mrlearning-base-ch1.md)」に従ってください (「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」の手順は除く)。これには、次の手順が含まれます。

1. [新しい Unity プロジェクトを作成](mrlearning-base-ch1.md#create-new-unity-project)して、適切な名前を付ける (たとえば、*MRTK Tutorials*)

2. [Windows Mixed Reality 用に Unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [TextMesh Pro の Essential Resources (重要なリソース) をインポートする](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Mixed Reality Toolkit をインポートする](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Mixed Reality Toolkit 用に Unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Mixed Reality Toolkit を Unity シーンに追加](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)し、シーンに適切な名前を付ける (たとえば、*AzureSpatialAnchors*)

次に、「[Mixed Reality Toolkit プロファイルを構成する方法 (空間認識表示オプションの変更)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)」の手順に従って、シーンの MRTK 構成プロファイルを **[DefaultHoloLens2ConfigurationProfile]** に変更し、空間認識メッシュの表示オプションを **[Occlusion]\(オクルージョン\)** に変更します。

> [!CAUTION]
> 上のリンクの「[Mixed Reality Toolkit 用に Unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)」の手順で述べられているように、MSBuild for Unity を有効にしないことを強くお勧めします。

## <a name="adding-inbuilt-unity-packages"></a>組み込み Unity パッケージの追加
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

このセクションでは、Unity の組み込み AR Foundation パッケージをインストールします。これは、次のセクションでインポートする Azure Spatial Anchors SDK で必要になるためです。

Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** を選択します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> AR Foundation パッケージが一覧に表示されるまでに数秒かかることがあります。

[Package Manager]\(パッケージ マネージャー\) ウィンドウで、 **[AR Foundation]** を選択し、 **[Install]\(インストール\)** ボタンをクリックしてパッケージをインストールします。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>チュートリアルのアセットのインポート

次の Unity カスタム パッケージを、**記載されている順で**ダウンロードして**インポート**します。

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (バージョン 2.1.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)

> [!TIP]
> Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」の手順を参照してください。

チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>シーンの作成と準備
<!-- TODO: Consider renaming to 'Preparing the scene' -->

このセクションでは、チュートリアルのプレハブをいくつか追加してシーンを準備します。

[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.AzureSpatialAnchors]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動します。 Ctrl ボタンを押したまま、 **[ButtonParent]** 、 **[DebugWindow]** 、 **[Instructions]** 、および **[ParentAnchor]** をクリックして 4 つのプレハブを選択します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

4 つのプレハブを選択したまま、[Hierarchy]\(階層\) ウィンドウにドラッグしてこれらをシーンに追加します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

シーン内のオブジェクトに焦点を合わせるには、ParentAnchor オブジェクトをダブルクリックして、もう一度少しズームアウトします。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> シーンに大きいアイコンが表示されている場合 (たとえば、大きいフレームの 'T' アイコンが邪魔になる場合)、<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">ギズモをオフに切り替える</a>ことによってこれらを非表示にすることができます。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>シーンを操作するためのボタンの構成

このセクションでは、スクリプトをシーンに追加して、ローカル アンカーと Azure Spatial Anchors の両方がアプリケーションでどのように動作するかの基本を示す一連のボタン イベントを作成します。

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1.Pressable Button Holo Lens 2 (Script) コンポーネントを構成する

[Hierarchy]\(階層\) ウィンドウで **[ButtonParent]** オブジェクトを展開し、 **[StartAzureSession]** という名前の最初の子オブジェクトを選択します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

[Inspector]\(インスペクター\) ウィンドウで **Pressable Button Holo Lens 2 (Script)** コンポーネントを見つけ、 **+** アイコンをクリックして、**Button Pressed ()** イベントに新しいイベント リスナーを追加します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

[Hierarchy]\(階層\) ウィンドウで [StartAzureSession] オブジェクトを選択した状態で、[Hierarchy]\(階層\) ウィンドウの **[ParentAnchor]** オブジェクトをクリックして、先ほど追加したイベント リスナーの空の **[None (Object)]\(なし (オブジェクト)\)** フィールドにドラッグして、このボタンで押されたボタン イベントを ParentAnchor オブジェクトがリッスンするようにします。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

同じイベント リスナーの **[No Function]\(関数なし\)** ドロップダウンをクリックし、 **[AnchorModuleScript]**  >  **[StartAzureSession ()]** を選択して、このボタンで押されたボタン イベントが発生したときにトリガーされるアクションとして StartAzureSession () 関数を設定します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2.Interactable (Script) コンポーネントを構成する

[Hierarchy]\(階層\) ウィンドウで [StartAzureSession] オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを見つけ、**OnClick ()** イベントについて上記の手順 1 と同じプロセス繰り返します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3.残りのボタンを構成する

残りの各ボタンについて、上記の手順 1 と手順 2 で説明したプロセスを完了して、**Button Pressed ()** と **OnClick ()** イベントの両方に関数を割り当てます。

* **[StopAzureSession]** オブジェクトについては、[AnchorModuleScript] > **[StopAzureSession ()]** 関数を割り当てます。
* **[CreateAzureAnchor]** オブジェクトについては、[AnchorModuleScript] > **[CreateAzureAnchor ()]** 関数を割り当てます。
  * 次に、 **[ParentAnchor]** を空の **[None (Game Object)]\(なし (ゲーム オブジェクト)\)** フィールドにもう一度ドラッグします。
* **[RemoveLocalAnchor]** オブジェクトについては、[AnchorModuleScript] > **[RemoveLocalAnchor ()]** 関数を割り当てます。
  * 次に、 **[ParentAnchor]** を空の **[None (Game Object)]\(なし (ゲーム オブジェクト)\)** フィールドにもう一度ドラッグします。
* **[FindAzureAnchor]** オブジェクトについては、[AnchorModuleScript] > **[FindAzureAnchor ()]** 関数を割り当てます。
* **[DeleteAzureAnchor]** オブジェクトについては、[AnchorModuleScript] > **[DeleteAzureAnchor ()]** 関数を割り当てます。

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4.シーンを Azure リソースに接続する

[Hierarchy]\(階層\) ウィンドウで **[ParentAnchor]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Spatial Anchor Manager (Script)** コンポーネントまでスクロールします。

次に、 **[Credentials]\(資格情報\)** セクションで、このチュートリアルの[前提条件](mrlearning-asa-ch1.md#prerequisites)の一部として作成した Spatial Anchors Account ID とキーを、対応する **[Spatial Anchors Account Id]\(Spatial Anchors アカウント ID\)** と **[Spatial Anchors Account Key]\(Spatial Anchors アカウント キー\)** フィールドに貼り付けます。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Azure Spatial Anchors の基本的な動作を試す

これで、Azure Spatial Anchors の基本を示すようにシーンが構成されたので、今度はアプリをデプロイして、Azure Spatial Anchors を直接体験できるようにします。

### <a name="1-add-additional-required-capabilities"></a>1.必要な機能をさらに追加する

Unity メニューで、 **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクト設定...\)** を選択し、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

[Player Settings]\(プレーヤーの設定\) ウィンドウで、 **[Player]\(プレーヤー\)** **[Publishing Settings]\(公開の設定\)** の順に選択します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

**[Publishing Settings]\(公開の設定\)** で、 **[Capabilities]\(機能\)** セクションまで下にスクロールして、チュートリアルの開始時にプロジェクトを作成したときに有効にした **InternetClient**、**Microphone**、および **SpatialPerception** の機能が有効になっていることを再確認します。 次に、**InternetClientServer**、**PrivateNetworkClientServer**、 **RemovableStorage**、および **Webcam** の機能を有効にします。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2.HoloLens 2 にアプリをデプロイする

Azure Spatial Anchors は Unity では実行できないため、Azure Spatial Anchors の機能をテストするには、プロジェクトをお使いのデバイスにデプロイする必要があります。

> [!TIP]
> HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」の手順を参照してください。

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3.HoloLens 2 でアプリを実行し、アプリ内の指示に従う

> [!CAUTION]
> Azure Spatial Anchors は、インターネットを使用してアンカー データの保存と読み込みを行うため、お使いのデバイスがインターネットに接続されていることを確認してください。

お使いのデバイスでアプリケーションが実行されているときに、Azure Spatial Anchor チュートリアルの手順パネルに表示される画面の指示に従います。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>エクスペリエンスの固定

前のセクションでは、Azure Spatial Anchors の基礎について学習しました。 キューブを使用して、アンカーがアタッチされた親のゲーム オブジェクトを表現および視覚化しました。 このセクションでは、エクスペリエンス全体を、ParentAnchor オブジェクトの子として配置して固定する方法について説明します。

### <a name="1-add-the-rocket-launcher-experience"></a>1.ロケット発射台エクスペリエンスを追加する

[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)**  >  **[RocketLauncher]** フォルダーに移動し、 **[RocketLauncher_Complete]** プレハブを選択します。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

[RocketLauncher_Complete] プレハブを選択したまま、[Hierarchy]\(階層\) ウィンドウの **ParentAnchor** オブジェクトの上にドラッグして、ParentAnchor オブジェクトの子にします。

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2.ロケット発射台エクスペリエンスの位置を変更する

**[RocketLauncher_Complete]** オブジェクトが適切なスケールと向きになるように配置、回転、拡大縮小しながら、**ParentAnchor** オブジェクトが引き続き表示されていることを確認します。次に例を示します。

* [Transform]\(変換\) の **[Position]\(位置\)** X = 0、Y = 0、Z = 3.75
* [Transform]\(変換\) の **[Rotation]\(回転\)** X = 0、Y = 90、Z = 0
* [Transform]\(変換\) の **[Scale]\(スケール\)** X = 10、Y = 10、Z = 10

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

アプリケーションでは、ユーザーがキューブを移動して、ロケット発射台エクスペリエンス全体を再配置できるようになりました。

> [!TIP]
> エクスペリエンスの再配置には、再配置オブジェクト (このチュートリアルで使用するキューブなど) の使用、エクスペリエンスを囲む境界ボックスを切り替えるボタンの使用、位置と回転のギズモの使用など、さまざまなユーザー エクスペリエンス フローがあります。

## <a name="congratulations"></a>結論

このチュートリアルでは、Azure Spatial Anchors の基礎について学習しました。 このチュートリアルでは、Azure Spatial Anchors セッションの開始と停止、単一のデバイス上での Azure Spatial Anchors の作成、アップロード、ダウンロードに必要なさまざまな手順を試すことができるいくつかのボタンが提供されました。

次のレッスンでは、Azure アンカー ID を HoloLens 2 に保存して (アプリケーションを再起動した後であっても) 取得できるようにする方法と、アンカー ID を複数のデバイス間で転送して空間的な位置合わせ行う方法について学習します。

[次のレッスン:2.Azure Spatial Anchors の保存、取得、および共有](mrlearning-asa-ch2.md)
