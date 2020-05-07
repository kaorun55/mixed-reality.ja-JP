---
title: マルチユーザー機能のチュートリアル - 1。 Photon Unity Networking の設定
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610712"
---
# <a name="1-setting-up-photon-unity-networking"></a>1.Photon Unity Networking の設定

## <a name="overview"></a>概要

このチュートリアルでは、Photon Unity Networking (PUN) を使用して共有エクスペリエンスの作成準備をする方法を学習します。 Photon は、Mixed Reality の開発者が共有エクスペリエンスを作成するために使用できるいくつかのネットワーク オプションの 1 つです。 Photon PUN アプリケーションの作成方法、Photon PUN アセットの Unity プロジェクトへのインポート方法、Unity プロジェクトの Photon PUN アプリケーションへの接続方法について説明します。

## <a name="objectives"></a>目標

* Photon PUN アプリケーションを作成する方法を学習する
* Photon PUN アセットを探してインポートする方法を学習する
* Unity プロジェクトを Photon PUN アプリケーションに接続する方法を学習する

## <a name="prerequisites"></a>前提条件

>[!TIP]
>[入門チュートリアル](mrlearning-base.md)と [Azure Spatial Anchors チュートリアル](mrlearning-asa-ch1.md)のチュートリアル シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。

* 正しい[ツールがインストールされている](install-the-tools.md)構成済みの Windows 10 PC
* Windows 10 SDK 10.0.18362.0 以降
* 基本的な C# プログラミング能力
* [開発用に構成された](using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス
* Unity 2019.2.X がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>
* 「[Spatial Anchors リソースを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクション ([クイック スタート:Azure Spatial Anchors を使用する Unity HoloLens アプリを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) チュートリアルにあります) を完了します。

> [!IMPORTANT]
> このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.2.X です。 これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。

## <a name="creating-and-preparing-the-unity-project"></a>Unity プロジェクトの作成と準備

このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備をします。

このためには、まず「[プロジェクトと最初のアプリケーションの初期化](mrlearning-base-ch1.md)」に従ってください (「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」の手順は除く)。これには、次の手順が含まれます。

1. [新しい Unity プロジェクトを作成](mrlearning-base-ch1.md#create-new-unity-project)して、適切な名前を付ける (たとえば、*MRTK Tutorials*)

2. [Windows Mixed Reality 用に Unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [TextMesh Pro の Essential Resources (重要なリソース) をインポートする](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Mixed Reality Toolkit をインポートする](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Mixed Reality Toolkit 用に Unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Mixed Reality Toolkit を Unity シーンに追加](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)し、シーンに適切な名前を付ける (たとえば、*MultiUserCapabilities*)

次に、「[Mixed Reality Toolkit プロファイルを構成する方法 (空間認識表示オプションの変更)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)」の手順に従って、シーンの MRTK 構成プロファイルを **[DefaultHoloLens2ConfigurationProfile]** に変更し、空間認識メッシュの表示オプションを **[Occlusion]\(オクルージョン\)** に変更します。

> [!CAUTION]
> 上のリンクの「[Mixed Reality Toolkit 用に Unity プロジェクトを構成する](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)」の手順で述べられているように、MSBuild for Unity を有効にしないことを強くお勧めします。

## <a name="configuring-the-capabilities"></a>機能の構成

Unity メニューで **[Edit]\(編集\)**  >  **[Project Settings]\(プロジェクトの設定\)** を選択して、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。次に、 **[Player]\(プレーヤー\)**  >   **[Publishing Settings]\(発行の設定\)** セクションを見つけます。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

**[Publishing Settings]\(公開の設定\)** で、 **[Capabilities]\(機能\)** セクションまで下にスクロールして、チュートリアルの開始時にプロジェクトを作成したときに有効にした **InternetClient**、**Microphone**、および **SpatialPerception** の機能が有効になっていることを再確認します。 次に、**InternetClientServer**、**PrivateNetworkClientServer**、**RemovableStorage** の機能を有効にします。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a>組み込み Unity パッケージの追加
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

このセクションでは、Unity の組み込み AR Foundation パッケージをインストールします。これは、次のセクションでインポートする Azure Spatial Anchors SDK で必要になるためです。

Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** を選択します。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> AR Foundation パッケージが一覧に表示されるまでに数秒かかることがあります。

[Package Manager]\(パッケージ マネージャー\) ウィンドウで、 **[AR Foundation]** を選択し、 **[Install]\(インストール\)** ボタンをクリックしてパッケージをインストールします。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>チュートリアルのアセットのインポート

次の Unity カスタム パッケージを、**記載されている順で**ダウンロードして**インポート**します。

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (バージョン 2.1.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」の手順を参照してください。

チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> MultiUserCapabilities チュートリアル アセット パッケージをインポートすると、型または名前空間が存在しないことを示すいくつかの [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) エラーが [Console]\(コンソール\) ウィンドウに表示されます。 これは想定されているものであり、次のセクションで Photon アセットをインポートする際に解決されます。

## <a name="importing-the-photon-assets"></a>Photon アセットをインポートする

このセクションでは、Photon Unity Network (PUN) アセットを Unity のアセット ストアからインポートします。

Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Asset Store]\(アセット ストア\)** を選択して [Asset Store]\(アセット ストア\) ウィンドウを開き、Exit Games から **[PUN 2 - FREE]** を検索して選択し、 **[Download]\(ダウンロード\)** ボタンをクリックしてアセット パッケージを自分の Unity アカウントにダウンロードします。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

ダウンロードが完了したら、 **[Import]\(インポート\)** ボタンをクリックして [Import Unity Package]\(Unity パッケージのインポート\) ウィンドウを開きます。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

Unity でインポート プロセスが完了したら、[Pun Wizard]\(Pun ウィザード\) ウィンドウが表示されて [PUN Setup]\(PUN 設定\) メニューが読み込まれます。今はこのウィンドウを無視するか、閉じて構いません。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a>Photon の設定

このセクションでは、Photon アカウントを作成 (まだ作成していない場合) し、新しい PUN アプリケーションを作成します。

使用したいアカウントが既にある場合は Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">ダッシュボード</a> に移動してサインインします。なければ、 **[こちらから作成してください]** リンクをクリックして手順に従い、新しいアカウントを登録します。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

サインインしたら、 **[Create a New App]\(新しいアプリの作成\)** ボタンをクリックします。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

[Create a New Application]\(新しいアプリケーションの作成\) ページで、次の値を入力します。

* [Photon Type]\(Photon の種別\) には、[Photon PUN] を選択します
* [Name]\(名前\) には、適切な名前 (_MRTK チュートリアル_ など) を入力します
* [Description]\(説明\) には、必要に応じて適切な説明を入力します
* "URL" フィールドは空のままにします

**[Create]\(作成する\)** をクリックして新しいアプリケーションを作成します。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

Photon で作成プロセスが完了すると、新しい PUN アプリケーションがダッシュボードに表示されます。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>Unity プロジェクトを PUN アプリケーションに接続する

このセクションでは、Unity プロジェクトを前のセクションで作成した PUN アプリケーションに接続します。

Photon ダッシュボードで、 **"App ID"(アプリ ID)** フィールドをクリックしてアプリ ID を表示し、クリップボードにコピーします。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Photon Unity Networking]**  >  **[PUN Wizard]\(PUN ウィザード\)** を選択して [Pun Wizard]\(Pun ウィザード\) ウィンドウを開き、 **[Setup Project]\(プロジェクトの設定\)** ボタンをクリックして [PUN Setup]\(PUN 設定\) メニューを開いて次のように構成します。

* **"AppId or Email"(アプリ ID またはメール)** フィールドで、前のステップでコピーした PUN アプリ ID を貼り付けます

**[Setup Project]\(プロジェクトの設定\)** ボタンをクリックしてアプリ ID を適用します。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

Unity で PUN 設定プロセスが完了すると、[PUN Setup]\(PUN 設定\) メニューに **[Done!]\(完了\)** というメッセージが表示され、 [Project]\(プロジェクト\) ウィンドウで **PhotonServerSettings** アセットが自動的に選択され、そのプロパティが [Inspector]\(インスペクター\) ウィンドウに表示されます。

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a>結論

Photon PUN アプリケーションを作成して、これを Unity プロジェクトに接続できました。 次の手順では、他のユーザーとの接続を許可して複数のユーザーが互いを見られるようにします。

[次のチュートリアル: 2.複数ユーザーの接続](mrlearning-sharing(photon)-ch2.md)
