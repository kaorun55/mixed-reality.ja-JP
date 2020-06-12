---
title: Azure Spatial Anchors チュートリアル - 4. Android と iOS 用の Azure Spatial Anchors
description: このチュートリアルを完了すると、Mixed Reality アプリケーション内で Azure Spatial Anchors を実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, コース, HoloLens, Azure, Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: 78fa6a2cdd29bd424ec3016a5467760063b87a14
ms.sourcegitcommit: 7011ac6fde80e5c45f04192fa1db6e1eb559e3b0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "84327940"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a>4.Android と iOS 用の Azure Spatial Anchors

このチュートリアルでは、AR Foundation、ARCore XR Plugin、ARKit XR Plugin を使用して、Android デバイスや iOS デバイス用にプロジェクトをビルドする方法について説明します。

## <a name="objectives"></a>目標

* Unity AR Foundation と ARCore XR Plugin を使用して、Android デバイス用にプロジェクトをビルドする方法について学習します。
* Unity AR Foundation と ARKit XR Plugin を使用して、iOS デバイス用にプロジェクトをビルドする方法について学習します。

> [!NOTE]
> このチュートリアルを完了するには、「Azure Spatial Anchors チュートリアル」 -> 「[Azure Spatial Anchors をお使いになる前に](mrlearning-asa-ch1.md)」を完了していることをご確認ください。

## <a name="adding-inbuilt-unity-packages"></a>組み込み Unity パッケージの追加

このセクションでは、Android デバイスと iOS デバイスをサポートするために必要な、Unity の組み込み AR Foundation、ARCore XR Plugin、ARKit XR Plugin の各パッケージをインストールします。

以下に示す、正しいバージョンの Unity パッケージがインストールされていることをご確認ください。

* **AR Foundation 2.1.4**
* **ARCore XR Plugin 2.2.0 プレビュー 2**
* **ARKit XR Plugin 2.1.1**

> [!NOTE]
> Android 用にこのプロジェクトを開発している場合は、ARKit XR Plugin パッケージをインストールする必要はありません。 同様に、iOS 用にこのプロジェクトを開発している場合は、ARCore XR Plugin をインストールする必要はありません。

Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** を選択します。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

すべてのパッケージが一覧に表示されるまでに数秒かかることがあります。 [Advanced]\(詳細設定\) オプションをクリックしてプレビュー パッケージを表示し、 **[Show preview packages]\(プレビュー パッケージを表示\)** を選択します。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

[Package Manager]\(パッケージ マネージャー\) ウィンドウで、 **[AR Foundation]** を選択します。表示される多くのバージョンから、**バージョン 2.1.4** を選択し、 **[Update to 2.1.4]\(2.1.4 に更新\)** をクリックしてそのパッケージを更新します。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

Android デバイスをサポートするには、同様のプロセスで、**ARCore XR Plugin 2.2.0 プレビュー 2** をインポートします。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

iOS デバイスをサポートするには、パッケージ マネージャーから **ARKit XR Plugin 2.1.1** Unity パッケージをインポートする必要があります。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a>AR Foundation カメラをサポートするように MRTK をカスタマイズする

次の手順で、AR Foundation をサポートするように MRTK 設定をカスタマイズできます。まず、[Hierarchy]\(階層\) ウィンドウで MixedRealityToolKit を選択し、[Inspector]\(インスペクター\) ウィンドウの [Mixed Reality ToolKit] で **[Clone]\(複製\)** をクリックします。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

**[Clone]\(複製\)** をクリックすると、新たに [Clone Profile]\(プロファイルの複製\) ウィンドウが表示されます。 **[Clone]\(複製\)** をもう一度クリックして、**DefaultMixedRealityToolkitProfile** を複製します。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

同様に、[インスペクター] ウィンドウで**カメラ プロファイル**を複製します。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

[インスペクター] ウィンドウで、MixedReality を見つけて、 **[カメラ]** タブを選択します。この [Inspector]\(インスペクター\) ウィンドウにある、[Camera Setting Providers]\(カメラ設定プロバイダー\) を展開し、 **[+Add Camera Setting Provider]\(+ カメラ設定プロバイダーの追加\)** をクリックして、 **[New data provider 1]\(新しいデータ プロバイダー 1\)** を展開します。次に、[Type]\(種類\) で **[None]\(なし\)** を選択し、 **[Microsoft.MixedReality.Toolkit.Experimental.UnityAR]** > **[UnityARCameraSettings]** の順に選択します。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

[Hierarchy]\(階層\) ウィンドウで MixedRealityToolKit オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウの **[コンポーネントの追加]** をクリックし、「AR reference Point manager」と入力して、そのスクリプトを選択することにより、サポート スクリプトをアタッチします。

**AR Reference Point Manager** スクリプトを追加すると、**AR Session Origin** も [Inspector]\(インスペクター\) ウィンドウに自動的に追加されます。 サポート スクリプトを追加すると、[Inspector]\(インスペクター\) ウィンドウは次のようになります。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-5.png)

## <a name="build-an-application-to-an-android-device"></a>アプリケーションを Android デバイス用にビルドする

このアプリケーションを Android デバイス用にビルドするには、ウィンドウの上部にある **[ファイル]** をクリックし、 **[ビルド設定]** を選択します。 画面に新しいウィンドウが表示されます。ここから、 **[Android]** を選択し、 **[Switch Platform]\(プラットフォームの切り替え\)** をクリックします。 プラットフォームの切り替えには数分かかります。 Android プラットフォームに切り替えた後、 **[Add Open Scenes]\(オープン シーンの追加\)** をクリックし、現在のシーンが **[Scenes in Build]\(ビルド内のシーン\)** リストで選択されている唯一のシーンであることを確認します。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

**[ビルド設定]** ウィンドウを閉じます。 Unity メニューで、[Mixed Reality Toolkit] > [Utilities]\(ユーティリティ\) > [Configure Unity Project]\(Unity プロジェクトの構成\) の順に選択し、 **[適用]** をクリックして、Android プラットフォーム用の Unity プロジェクトを構成します。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

Unity メニューで、 **[編集]**  >  **[Project Settings]\(プロジェクト設定\)** の順に選択し、[Project Settings]\(プロジェクト設定\) ウィンドウを開きます。 [Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレーヤー\)** タブを選択し、 **[Other Settings]\(その他の設定\)** セクションを展開して、 **[Vulkan]** を選択し、" **-** " 記号をクリックしてこれを削除します。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

**[Player Settings]\(プレーヤーの設定\)** ウィンドウを閉じ、もう一度 **[ビルド設定]** ウィンドウを開きます。 次に、USB ケーブルを使用して、Android デバイスをコンピューターに接続し、ドロップダウンの **[ビルドして実行]** でお使いのデバイスを選択して、 **[ビルドして実行]** をクリックします。 .apk ファイルを保存するように求められます。このファイルの名前は任意に選択できます。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> Unity コンソール ウィンドウに、Android SDK、NDK、JDK モジュールに関連するエラーが表示される場合は、Unity ハブを開き、その Android ビルド サポート モジュール用の関連する SDK、NDK、JDK モジュールをインストールする必要があります。

ビルド プロセスが完了すると、アプリケーションが Android デバイスに自動的に読み込まれます。

## <a name="build-an-application-to-ios-device"></a>アプリケーションを iOS デバイス用にビルドする

このアプリケーションを iOS デバイス用にビルドするには、ウィンドウの上部にある **[ファイル]** をクリックし、 **[ビルド設定]** を選択します。 画面に新しいウィンドウが表示されます。ここから、 **[iOS]** を選択し、 **[Switch Platform]\(プラットフォームの切り替え\)** をクリックします。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

**[ビルド設定]** ウィンドウを閉じます。 Unity メニューで、[Mixed Reality Toolkit] > [Utilities]\(ユーティリティ\) > [Configure Unity Project]\(Unity プロジェクトの構成\) の順に選択し、 **[適用]** をクリックして、iOS プラットフォーム用の Unity プロジェクトを構成します。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

iOS Xcode プロジェクトをビルドするには、[ビルド設定] に移動し、 **[ビルド]** をクリックします。

このプロジェクトをお使いの iOS デバイスにデプロイする方法については、[このガイド](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)を参照してください。

## <a name="congratulations"></a>結論

このチュートリアルでは、Android デバイスや iOS デバイス用にプロジェクトをビルドする方法について学習しました。 また、AR Foundation、ARCore XR Plugin、ARKit XR Plugin を使用して、プロジェクトが Android デバイスや iOS デバイスで動作するようにする方法についても学習しました。
