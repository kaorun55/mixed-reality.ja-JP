---
title: Azure Spatial Anchors チュートリアル - 4. Android と iOS 用の Azure Spatial Anchors
description: このチュートリアルを完了すると、Mixed Reality アプリケーション内で Azure Spatial Anchors を実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, コース, HoloLens, Azure, Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: a35f73ae5aee493182f0f4990aa345d990c3f513
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/26/2020
ms.locfileid: "83867624"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="2fbfd-105">4.Android と iOS 用の Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="2fbfd-105">4. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="2fbfd-106">このチュートリアルでは、AR Foundation、ARCore XR Plugin、ARKit XR Plugin を使用して、Android デバイスや iOS デバイス用にプロジェクトをビルドする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="2fbfd-107">目標</span><span class="sxs-lookup"><span data-stu-id="2fbfd-107">Objectives</span></span>

* <span data-ttu-id="2fbfd-108">Unity AR Foundation と ARCore XR Plugin を使用して、Android デバイス用にプロジェクトをビルドする方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-108">Learn how to build your project to Android device using Unity AR Foundation and ARCore XR Plugin.</span></span>
* <span data-ttu-id="2fbfd-109">Unity AR Foundation と ARKit XR Plugin を使用して、iOS デバイス用にプロジェクトをビルドする方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-109">Learn how to build your project to an iOS device using Unity AR Foundation and ARKit XR Plugin.</span></span>

[!NOTE] <span data-ttu-id="2fbfd-110">このチュートリアルを完了するには、「Azure Spatial Anchors チュートリアル」 -> 「[Azure Spatial Anchors をお使いになる前に](mrlearning-asa-ch1.md)」を完了していることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-110">To complete this tutorial, make sure you have completed Azure Spatial Anchors Tutorials -> [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md).</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="2fbfd-111">組み込み Unity パッケージの追加</span><span class="sxs-lookup"><span data-stu-id="2fbfd-111">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="2fbfd-112">このセクションでは、Android デバイスと iOS デバイスをサポートするために必要な、Unity の組み込み AR Foundation、ARCore XR Plugin、ARKit XR Plugin の各パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-112">In this section, you will install Unity's inbuilt AR Foundation, ARCore XR Plugin, and ARKit XR Plugin packages required to support Android and iOS devices.</span></span>

<span data-ttu-id="2fbfd-113">以下に示す、正しいバージョンの Unity パッケージがインストールされていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-113">Make sure you install the correct version of these Unity packages as listed below:</span></span>

* <span data-ttu-id="2fbfd-114">**AR Foundation 2.1.4**</span><span class="sxs-lookup"><span data-stu-id="2fbfd-114">**AR Foundation 2.1.4**</span></span>
* <span data-ttu-id="2fbfd-115">**ARCore XR Plugin 2.2.0 プレビュー 2**</span><span class="sxs-lookup"><span data-stu-id="2fbfd-115">**ARCore XR plugin 2.2.0 preview 2**</span></span>
* <span data-ttu-id="2fbfd-116">**ARKit XR Plugin 2.1.1**</span><span class="sxs-lookup"><span data-stu-id="2fbfd-116">**ARKit XR plugin 2.1.1**</span></span>

[!NOTE] <span data-ttu-id="2fbfd-117">Android 用にこのプロジェクトを開発している場合は、ARKit XR Plugin パッケージをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-117">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="2fbfd-118">同様に、iOS 用にこのプロジェクトを開発している場合は、ARCore XR Plugin をインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-118">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

<span data-ttu-id="2fbfd-119">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-119">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

<span data-ttu-id="2fbfd-121">すべてのパッケージが一覧に表示されるまでに数秒かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-121">It might take a few seconds before all packages appear in the list.</span></span> <span data-ttu-id="2fbfd-122">[Advanced]\(詳細設定\) オプションをクリックしてプレビュー パッケージを表示し、 **[Show preview packages]\(プレビュー パッケージを表示\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-122">Display preview packages by clicking on Advanced option and select "**Show preview packages.**"</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

<span data-ttu-id="2fbfd-124">[Package Manager]\(パッケージ マネージャー\) ウィンドウで、 **[AR Foundation]** を選択します。表示される多くのバージョンから、バージョン 2.1.4 を選択し、 **[Update to 2.1.4]\(2.1.4 に更新\)** をクリックしてそのパッケージを更新します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-124">In the Package Manager window, select **AR Foundation**, here you see many version and need to select version 2.1.4 and update the package by clicking the **Update to 2.1.4** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

<span data-ttu-id="2fbfd-126">Android デバイスをサポートするには、同様のプロセスで、ARCore XR Plugin 2.2.0 プレビュー 2 をインポートします。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-126">To support Android devices, follow the same process to import ARCore XR Plugin 2.2.0 preview 2.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

<span data-ttu-id="2fbfd-128">iOS デバイスをサポートするには、パッケージ マネージャーから **ARKit XR Plugin 2.1.1** Unity パッケージをインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-128">To support iOS devices, you should import the **ARKit XR plugin 2.1.1** Unity package from the Package Manager.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a><span data-ttu-id="2fbfd-130">AR Foundation カメラをサポートするように MRTK をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="2fbfd-130">Customize MRTK to support AR Foundation camera</span></span>

<span data-ttu-id="2fbfd-131">次の手順で、AR Foundation をサポートするように MRTK 設定をカスタマイズできます。まず、[Hierarchy]\(階層\) ウィンドウで MixedRealityToolKit を選択し、[Inspector]\(インスペクター\) ウィンドウの [Mixed Reality ToolKit] で **[Clone]\(複製\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-131">Customize MRTK settings to support AR Foundation by selecting MixedRealityToolKit in the Hierarchy window and click the **Clone** button in Mixed Reality ToolKit in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

<span data-ttu-id="2fbfd-133">**[Clone]\(複製\)** をクリックすると、新たに [Clone Profile]\(プロファイルの複製\) ウィンドウが表示されます。[Clone]\(複製\) をもう一度クリックして、DefaultMixedRealityToolkitProfile を複製します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-133">When you click the **Clone** button, a new Clone Profile window will appear, click on the Clone button again to clone the DefaultMixedRealityToolkitProfile.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

<span data-ttu-id="2fbfd-135">同様に、[Inspector]\(インスペクター\) ウィンドウでカメラ プロファイルを複製し、プロファイルの名前を "UnityARConfigurationProfile" に変更して、 **[Clone]\(複製\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-135">Similarly, clone the camera profile in the Inspector window and rename the profile to “UnityARConfigurationProfile” and click on the **Clone** button.</span></span> <span data-ttu-id="2fbfd-136">[Inspector]\(インスペクター\) ウィンドウで、MixedReality を見つけて、[カメラ] タブを選択します。この [Inspector]\(インスペクター\) ウィンドウにある、[Camera Setting Providers]\(カメラ設定プロバイダー\) を展開し、 **[+Add Camera Setting Provider]\(+ カメラ設定プロバイダーの追加\)** をクリックして、 **[New data provider 1]\(新しいデータ プロバイダー 1\)** を展開します。次に、[Type]\(種類\) で **[None]\(なし\)** を選択し、 **[Microsoft .MixedReality.Toolkit.Experimental.UnityAR]** > **[UnityARCameraSettings]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-136">In the Inspector window, locate the MixedReality, select the Camera tab Expand the camera setting providers in the inspector window and click on **+Add Camera Setting Provider** > expand **New data provider 1**> select Type **None** >select **Microsoft .MixedReality.Toolkit.Experimental.UnityAR** > Select **UnityARCameraSettings**.</span></span>


![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

<span data-ttu-id="2fbfd-138">[Hierarchy]\(階層\) ウィンドウで MixedRealityToolKit オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウの **[コンポーネントの追加]** をクリックし、「AR reference Point manager」と入力して、そのスクリプトを選択することにより、サポート スクリプトをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-138">With the MixedRealityToolKit object selected in the Hierarchy window, in the Inspector window, attach supporting scripts by clicking on the **Add component** button and type in AR reference Point manager and select the script.</span></span>

<span data-ttu-id="2fbfd-139">AR Reference Point Manager スクリプトを追加すると、AR Session Origin も [Inspector]\(インスペクター\) ウィンドウに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-139">Adding the  "AR Reference Point Manager" script will automatically add "AR session origin" along with it in the Inspector window.</span></span> <span data-ttu-id="2fbfd-140">サポート スクリプトを追加すると、[Inspector]\(インスペクター\) ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-140">After adding the supporting scripts, the Inspector window should look like this.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

## <a name="build-application-to-android-device"></a><span data-ttu-id="2fbfd-142">アプリケーションを Android デバイス用にビルドする</span><span class="sxs-lookup"><span data-stu-id="2fbfd-142">Build application to Android device</span></span>

<span data-ttu-id="2fbfd-143">このアプリケーションを Android デバイス用にビルドするには、ウィンドウの上部にある **[ファイル]** をクリックし、 **[ビルド設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-143">To build this application to your Android device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="2fbfd-144">画面に新しいウィンドウが表示されます。ここから、 **[Android]** を選択し、 **[Switch Platform]\(プラットフォームの切り替え\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-144">A new window will appear on the screen, select **Android,** and click on the **Switch Platform**.</span></span> <span data-ttu-id="2fbfd-145">プラットフォームの切り替えには数分かかります。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-145">It will take a few minutes to switch platform.</span></span> <span data-ttu-id="2fbfd-146">Android プラットフォームに切り替えた後、 **[Add Open Scenes]\(オープン シーンの追加\)** をクリックし、現在のシーンが **[Scenes in Build]\(ビルド内のシーン\)** リストで選択されている唯一のシーンであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-146">After switching to the Android platform, click on **Add Open Scenes** and make sure your current scene is the only selected scene in the **Scenes In Build** list.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

<span data-ttu-id="2fbfd-148">**[ビルド設定]** ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-148">Close the **Build Settings** window.</span></span> <span data-ttu-id="2fbfd-149">Unity メニューで、**Mixed Reality Toolkit** >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** の順に選択し、 **[適用]** をクリックして、Android プラットフォーム用の Unity プロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-149">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click on **Apply** to configure the Unity project for the Android platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

<span data-ttu-id="2fbfd-151">Unity メニューで、 **[編集]**  >  **[Project Settings]\(プロジェクト設定\)** の順に選択し、[Project Settings]\(プロジェクト設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-151">In the Unity menu, select **Edit** > **Project Settings** to open the Project Settings window.</span></span> <span data-ttu-id="2fbfd-152">[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレーヤー\)** タブを選択し、[Other Settings]\(その他の設定\) セクションを展開して、 **[Vulkan]** を選択し、"-" 記号をクリックしてこれを削除します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-152">In the Project Settings, window selects the **Player** tab, expand the Other Settings section, select **Vulkan,** and remove it by clicking the "-" symbol.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

<span data-ttu-id="2fbfd-154">[Player Settings]\(プレーヤーの設定\) ウィンドウを閉じ、もう一度 [ビルド設定] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-154">Close the Player Settings window and open the Build Settings window again.</span></span> <span data-ttu-id="2fbfd-155">次に、USB ケーブルを使用して、Android デバイスをコンピューターに接続し、ドロップダウンの **[ビルドして実行]** でお使いのデバイスを選択して、 **[ビルドして実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-155">Then, using a USB cable, connect your Android device to your computer and select your device in the **Build and Run on** the dropdown, then click **Build And Run**.</span></span> <span data-ttu-id="2fbfd-156">.apk ファイルを保存するように求められます。このファイルの名前は任意に選択できます。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-156">You will be asked to save a .apk file, which you can pick any name.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> <span data-ttu-id="2fbfd-158">Unity コンソール ウィンドウに、Android SDK、NDK、JDK モジュールに関連するエラーが表示される場合は、Unity ハブを開き、その Android ビルド サポート モジュール用の関連する SDK、NDK、JDK モジュールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-158">If you get any error in the Unity Console window related to Android SDK, NDK, and or JDK modules, you need to open Unity Hub and install the associated SDK, NDK, and JDK modules for the Android Build Support module.</span></span>

<span data-ttu-id="2fbfd-159">ビルド プロセスが完了すると、アプリケーションが Android デバイスに自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-159">When the build process is complete, your applications should automatically load on your Android device.</span></span>

## <a name="build-application-to-ios-device"></a><span data-ttu-id="2fbfd-160">アプリケーションを iOS デバイス用にビルドする</span><span class="sxs-lookup"><span data-stu-id="2fbfd-160">Build application to iOS Device</span></span>

<span data-ttu-id="2fbfd-161">このアプリケーションを iOS デバイス用にビルドするには、ウィンドウの上部にある **[ファイル]** をクリックし、 **[ビルド設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-161">To build this application to your iOS device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="2fbfd-162">画面に新しいウィンドウが表示されます。ここから、 **[iOS]** を選択し、 **[Switch Platform]\(プラットフォームの切り替え\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-162">A new window will appear on the screen, then select **iOS** and click on the **Switch Platform**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

<span data-ttu-id="2fbfd-164">**[ビルド設定]** ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-164">Close the **Build Settings** window.</span></span> <span data-ttu-id="2fbfd-165">Unity メニューで、**Mixed Reality Toolkit** >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** の順に選択し、 **[適用]** をクリックして、iOS プラットフォーム用の Unity プロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-165">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click on **Apply** to configure the Unity project for the iOS platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

<span data-ttu-id="2fbfd-167">iOS Xcode プロジェクトをビルドするには、[ビルド設定] に移動し、 **[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-167">To build the iOS XCode project, go to Build Settings and, click on **Build**.</span></span>

<span data-ttu-id="2fbfd-168">このプロジェクトをお使いの iOS デバイスにデプロイする方法については、[このガイド](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-168">Follow [this guide](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) to learn how to deploy this project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2fbfd-169">結論</span><span class="sxs-lookup"><span data-stu-id="2fbfd-169">Congratulations</span></span>

<span data-ttu-id="2fbfd-170">このチュートリアルでは、Android デバイスや iOS デバイス用にプロジェクトをビルドする方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-170">In this tutorial, you learned how to build your project for Android and iOS devices.</span></span> <span data-ttu-id="2fbfd-171">また、AR Foundation、ARCore XR Plugin、ARKit XR Plugin を使用して、プロジェクトが Android デバイスや iOS デバイスで動作するようにする方法についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="2fbfd-171">You also learned how to use AR Foundation, ARCore XR Plugin, and ARKit XR Plugin to make your project work for Android and iOS devices.</span></span>