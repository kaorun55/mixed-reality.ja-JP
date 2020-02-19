---
title: 入門チュートリアル -2. プロジェクトと最初のアプリケーションの初期化
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: d3392df9bfad5938d71d3a01999be51834a98a5d
ms.sourcegitcommit: 87aca9c2b73b0e83cb70a46443dcdb08c3621005
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77373444"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="ec90f-105">2.プロジェクトと最初のアプリケーションの初期化</span><span class="sxs-lookup"><span data-stu-id="ec90f-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="ec90f-106">概要</span><span class="sxs-lookup"><span data-stu-id="ec90f-106">Overview</span></span>

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
<span data-ttu-id="ec90f-107">この最初のチュートリアルでは、<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality ツールキット (MRTK) </a>によって提供されるいくつかの機能について学習し、HoloLens 2 用の最初のアプリケーションを起動してデバイスにデプロイします。</span><span class="sxs-lookup"><span data-stu-id="ec90f-107">In this first tutorial, you will learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="ec90f-108">目標</span><span class="sxs-lookup"><span data-stu-id="ec90f-108">Objectives</span></span>

* <span data-ttu-id="ec90f-109">HoloLens 開発用に Unity を構成する</span><span class="sxs-lookup"><span data-stu-id="ec90f-109">Configure Unity for HoloLens development</span></span>
* <span data-ttu-id="ec90f-110">アセットをインポートし、シーンをセットアップする</span><span class="sxs-lookup"><span data-stu-id="ec90f-110">Import assets and set up the scene</span></span>
* <span data-ttu-id="ec90f-111">空間マッピングのメッシュ、ハンド メッシュ、およびフレームレート カウンターを視覚化する</span><span class="sxs-lookup"><span data-stu-id="ec90f-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ec90f-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="ec90f-112">Prerequisites</span></span>

* <span data-ttu-id="ec90f-113">正しい[ツールがインストールされている](install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="ec90f-113">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="ec90f-114">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="ec90f-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="ec90f-115">基本的な C# プログラミング能力</span><span class="sxs-lookup"><span data-stu-id="ec90f-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="ec90f-116">[開発用に構成された](using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="ec90f-116">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="ec90f-117">Unity 2019.2.X がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="ec90f-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec90f-118">このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.2.X です。</span><span class="sxs-lookup"><span data-stu-id="ec90f-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="ec90f-119">これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="ec90f-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="ec90f-120">新しい Unity プロジェクトを作成します</span><span class="sxs-lookup"><span data-stu-id="ec90f-120">Create new Unity project</span></span>

<span data-ttu-id="ec90f-121">**Unity Hub** を起動し、 **[Projects]\(プロジェクト\)** タブを選択し、 **[New]\(新規\)** ボタンの横にある**下矢印**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec90f-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

<span data-ttu-id="ec90f-123">上の「[前提条件](#prerequisites)」セクションで指定されている Unity のバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-123">Select the Unity version specified in the [Prerequisites](#prerequisites) section above:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

<span data-ttu-id="ec90f-125">[Create a new project]\(新規プロジェクトの作成\) ウィンドウで、以下のようにします。</span><span class="sxs-lookup"><span data-stu-id="ec90f-125">In the Create a new project window:</span></span>

* <span data-ttu-id="ec90f-126">**[Templates]\(テンプレート\)** が **3D** に設定されていることを確認します</span><span class="sxs-lookup"><span data-stu-id="ec90f-126">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="ec90f-127">"_MRTK チュートリアル_" など、適切な **[Project Name]\(プロジェクト名\)** を入力します</span><span class="sxs-lookup"><span data-stu-id="ec90f-127">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="ec90f-128">プロジェクトを格納するための適切な **[Location]\(場所\)** を選択します。たとえば、_D:\MixedRealityLearning_ など</span><span class="sxs-lookup"><span data-stu-id="ec90f-128">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="ec90f-129">**[Create]\(作成\)** ボタンをクリックして、新しい Unity プロジェクトを作成して起動します</span><span class="sxs-lookup"><span data-stu-id="ec90f-129">Click the **Create** button to create and launch your new Unity project</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="ec90f-131">Windows で作業している場合は、255 文字の MAX_PATH 制限があります。</span><span class="sxs-lookup"><span data-stu-id="ec90f-131">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="ec90f-132">Unity はこれらの制限の影響を受け、255 文字を超えるファイル パスが存在する場合、コンパイルに失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec90f-132">Unity is affected by these limits and may fail to compile if any file path is longer than 255 characters.</span></span> <span data-ttu-id="ec90f-133">そのため、できるだけドライブのルートの近くに Unity プロジェクトを保存することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec90f-133">Consequently, it is strongly recommended to store your Unity project as close to the root of the drive as possible.</span></span>

<span data-ttu-id="ec90f-134">Unity によってプロジェクトが作成されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-134">Wait for Unity to create the project:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="ec90f-136">Windows Mixed Reality 用に Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="ec90f-136">Configure the Unity project for Windows Mixed Reality</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="ec90f-137">このセクションでは、ビルド プラットフォームの切り替え、仮想現実の有効化、および空間認知の有効化を行います。</span><span class="sxs-lookup"><span data-stu-id="ec90f-137">In this section, you will switch build platform, enable virtual reality, and enable spatial perception.</span></span>

### <a name="1-switch-build-platform"></a><span data-ttu-id="ec90f-138">1.ビルド プラットフォームの切り替え</span><span class="sxs-lookup"><span data-stu-id="ec90f-138">1. Switch build platform</span></span>

<span data-ttu-id="ec90f-139">Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** を選択し、[Build Settings]\(ビルド設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

<span data-ttu-id="ec90f-141">[Build Settings]\(ビルド設定\) ウィンドウで、 **[Universal Windows Platform]\(ユニバーサル Windows プラットフォーム\)** を選択して、 **[Switch Platform]\(プラットフォームの切り替え\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec90f-141">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

<span data-ttu-id="ec90f-143">Unity がプラットフォームの切り替えを完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-143">Wait for Unity to finish switching the platform:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

<span data-ttu-id="ec90f-145">Unity でプラットフォームの切り替えが完了したら、赤色の **x** アイコンをクリックして、[Build Settings]\(ビルド設定\) ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-145">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a><span data-ttu-id="ec90f-147">2.仮想現実を有効にする</span><span class="sxs-lookup"><span data-stu-id="ec90f-147">2. Enable virtual reality</span></span>

> [!NOTE]
> <span data-ttu-id="ec90f-148">仮想現実を有効にすることは、立体視 (それぞれの目で異なる画像をレンダリングする) を有効にすることを指すため、複合現実および拡張現実ヘッドセットにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-148">Enabling virtual reality also applies to mixed reality and augmented reality headsets because it refers to enabling stereoscopic vision, i.e. rendering different images for each eye.</span></span>

<span data-ttu-id="ec90f-149">Unity メニューで、 **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクト設定...\)** を選択し、[Project Settings]\(プロジェクト設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-149">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

<span data-ttu-id="ec90f-151">[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレイヤー\)**  >  **[XR Settings]\(XR 設定\)** を選択して、XR の設定を展開します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-151">In the Project Settings window, select **Player** > **XR Settings** to expand the XR Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

<span data-ttu-id="ec90f-153">[XR Settings]\(XR 設定\) で、 **[Virtual Reality Supported]\(仮想現実がサポートされている\)** チェックボックスをオンにして、仮想現実を有効にします。次に、 **+** アイコンをクリックし、 **[Windows Mixed Reality]** を選択して Windows Mixed Reality SDK を追加します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-153">In the XR Settings, check the **Virtual Reality Supported** checkbox to enable virtual reality, then click the **+** icon and select **Windows Mixed Reality** to add the Windows Mixed Reality SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

<span data-ttu-id="ec90f-155">Unity が SDK の追加を完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-155">Wait for Unity to finish adding the SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

<span data-ttu-id="ec90f-157">Unity で SDK の追加が完了したら、次のように XR の設定を最適化します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-157">When Unity has finished adding the SDK, optimize the XR Settings as follows:</span></span>

* <span data-ttu-id="ec90f-158">Windows Mixed Reality の **[Depth Format]\(深度形式\)** を **[16-bit depth]\(16 ビット深度\)** に設定します</span><span class="sxs-lookup"><span data-stu-id="ec90f-158">Set Windows Mixed Reality **Depth Format** to **16-bit depth**</span></span>
* <span data-ttu-id="ec90f-159">Windows Mixed Reality の **[Enable Depth Sharing]\( 深度の共有を有効にする\)** チェックボックスをオンにします</span><span class="sxs-lookup"><span data-stu-id="ec90f-159">Check the Windows Mixed Reality **Enable Depth Sharing** checkbox</span></span>
* <span data-ttu-id="ec90f-160">**[Stereo Rendering Mode]\(ステレオ レンダリング モード\)\*** を **[Single Pass Instanced]\(シングル パス インスタンス\)** に設定します</span><span class="sxs-lookup"><span data-stu-id="ec90f-160">Set Stereo **Rendering Mode\*** to **Single Pass Instanced**</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> <span data-ttu-id="ec90f-162">Unity を Windows Mixed Reality 向けに最適化する方法の詳細については、「[Unity の推奨設定](recommended-settings-for-unity.md)」ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec90f-162">To learn more about optimizing Unity for Windows Mixed Reality, you can refer to the [Recommended settings for Unity](recommended-settings-for-unity.md) documentation.</span></span>

### <a name="3-enable-spatial-perception"></a><span data-ttu-id="ec90f-163">3.空間認知を有効にする</span><span class="sxs-lookup"><span data-stu-id="ec90f-163">3. Enable spatial perception</span></span>

> [!NOTE]
> <span data-ttu-id="ec90f-164">空間認知を使用すると、Windows Mixed Reality デバイス上で空間マッピングのメッシュを視覚化できます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-164">Spatial perception allows visualization of the spatial mapping mesh on Windows Mixed Reality devices.</span></span>

<span data-ttu-id="ec90f-165">[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレイヤー\)**  >  **[Publishing Settings]\(公開設定\)** を選択して、公開の設定を展開します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-165">In the Project Settings window, select **Player** > **Publishing Settings** to expand the Publishing Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

<span data-ttu-id="ec90f-167">[Publishing Settings]\(公開設定\)で、 **[Capabilities]\(機能\)** セクションまで下にスクロールし、 **[SpatialPerception]** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="ec90f-167">In the Publishing Settings, scroll down to the **Capabilities** section and check the **SpatialPerception** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

<span data-ttu-id="ec90f-169">[Project Settings]\(プロジェクト設定\) ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-169">Close the Project Settings window.</span></span>

## <a name="import-textmesh-pro-essential-resources"></a><span data-ttu-id="ec90f-170">TextMesh Pro の重要なリソースをインポートする</span><span class="sxs-lookup"><span data-stu-id="ec90f-170">Import TextMesh Pro Essential Resources</span></span>

> [!NOTE]
> <span data-ttu-id="ec90f-171">このパッケージは、Mixed Reality Toolkit の UI 要素で必要とされるためインポートします。</span><span class="sxs-lookup"><span data-stu-id="ec90f-171">We are importing this package because it is required by Mixed Reality Toolkit's UI elements.</span></span>

<span data-ttu-id="ec90f-172">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[TextMeshPro]**  >  **[Import TMP Essential Resources]\(TMP の重要なリソースをインポート\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-172">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

<span data-ttu-id="ec90f-174">[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="ec90f-174">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="ec90f-176">Mixed Reality ツールキットをインポートする</span><span class="sxs-lookup"><span data-stu-id="ec90f-176">Import the Mixed Reality Toolkit</span></span>

<span data-ttu-id="ec90f-177">Unity カスタム パッケージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="ec90f-177">Download the Unity custom package:</span></span>

* [<span data-ttu-id="ec90f-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="ec90f-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.2.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage)

<span data-ttu-id="ec90f-179">Unity メニューで、 **[Assets]\(アセット\)**  >  **[Import Package]\(パッケージのインポート\)**  >  **[Custom Package...]\(カスタム パッケージ...\)** を選択して [Import package...]\(パッケージのインポート...\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-179">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

<span data-ttu-id="ec90f-181">[Import package...]\(パッケージのインポート...\) ウィンドウで、ダウンロードした **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage** を選択し、 **[Open]\(開く\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec90f-181">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

<span data-ttu-id="ec90f-183">[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="ec90f-183">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a><span data-ttu-id="ec90f-185">Mixed Reality ツールキット用に Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="ec90f-185">Configure the Unity project for the Mixed Reality Toolkit</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="ec90f-186">パッケージがインポートされると、[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-186">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="ec90f-187">表示されていない場合は、Unity メニューの **[Mixed Reality Toolkit]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** を選択して開きます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-187">If it does not, open it by selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** in the Unity menu.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

<span data-ttu-id="ec90f-189">[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウで、 **[Modify Configurations]\(構成の変更\)** セクションを展開し、 **[Enable MSBuild for Unity]\(MSBuild for Unity を有効にする\)** チェックボックスを<u>オフ</u>にし、他のすべてのオプションがオンになっていることを確認し、 **[Apply]\(適用\)** ボタンをクリックして設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-189">In the MRTK Project Configurator window, expand the **Modify Configurations** section, <u>uncheck</u> the **Enable MSBuild for Unity** checkbox, ensure all other options are checked, and click the **Apply** button to apply the settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="ec90f-191">MSBuild for Unity は使用するすべての SDK をサポートしていない場合があり、有効にした後は無効にするのが困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="ec90f-191">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="ec90f-192">そのため、MSBuild for Unity を有効にしないことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec90f-192">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="ec90f-193">Mixed Reality ツールキットを構成する</span><span class="sxs-lookup"><span data-stu-id="ec90f-193">Configure the Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

<span data-ttu-id="ec90f-194">Unity メニューで、 **[Mixed Reality Toolkit]\(Mixed Reality ツールキット\)**  >  **[Add to Scene and Configure...]\(シーンに追加して構成する...\)** の順に選択して、Mixed Reality ツールキットを現在のシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-194">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the Mixed Reality Toolkit to your current scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

<span data-ttu-id="ec90f-196">[Hierarchy]\(階層\) ウィンドウで MixedRealityToolkit オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、Mixed Reality ツールキットの構成プロファイルを **DefaultHoloLens2ConfigurationProfile** に変更します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-196">With the MixedRealityToolkit object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit configuration profile to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

<span data-ttu-id="ec90f-198">Unity メニューで、 **[File]\(ファイル\)**  >  **[Save As...]\(名前を付けて保存...\)** を選択して [Save Scene]\(シーンの保存\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-198">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

<span data-ttu-id="ec90f-200">[Save Scene]\(シーンの保存\) ウィンドウで、プロジェクトの **[Scenes]\(シーン\)** フォルダーに移動し、シーンに適切な名前を付け (たとえば、_はじめに_)、 **[Save]\(保存\)** ボタンをクリックしてシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-200">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _Getting Started_, and click the **Save** button to save the scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="ec90f-202">デバイスへのアプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="ec90f-202">Build your application to your device</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="ec90f-203">1.Unity プロジェクトのビルド</span><span class="sxs-lookup"><span data-stu-id="ec90f-203">1. Build the Unity project</span></span>

<span data-ttu-id="ec90f-204">Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** を選択し、[Build Settings]\(ビルド設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-204">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="ec90f-205">[Build Settings]\(ビルド設定\) ウィンドウで、 **[Add Open Scenes]\(開いているシーンを追加する\)** ボタンをクリックして、 **[Scenes In Build]\(ビルド内のシーン\)** リストの現在のシーンを追加します。次に **[Build]\(ビルド\)** ボタンをクリックして、[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-205">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

<span data-ttu-id="ec90f-207">[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウで、ビルドを格納する適切な場所 (たとえば _D:\MixedRealityLearning\Builds_) を選択し、新しいフォルダーを作成して適切な名前 (たとえば _GettingStarted_) を付け、 **[Select Folder]\(フォルダーの選択\)** ボタンをクリックしてビルド処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-207">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

<span data-ttu-id="ec90f-209">Unity がビルド処理を完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-209">Wait for Unity to finish the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="ec90f-211">2.アプリのビルドと配置</span><span class="sxs-lookup"><span data-stu-id="ec90f-211">2. Build and deploy the application</span></span>

<span data-ttu-id="ec90f-212">ビルド処理が完了すると、Unity は、ビルドを格納した場所を開くように Windows ファイル エクスプローラーを表示します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-212">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="ec90f-213">フォルダー内を移動し、ソリューション ファイルをダブルクリックして Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-213">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> <span data-ttu-id="ec90f-215">Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、[「ツールのインストール」](install-the-tools.md)ドキュメントで示されている、前提条件となるすべてのコンポーネントがインストールされていることを確認してください</span><span class="sxs-lookup"><span data-stu-id="ec90f-215">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the [Install the Tools](install-the-tools.md) documentation.</span></span>

<span data-ttu-id="ec90f-216">**[マスター]** または **[リリース]** 構成、 **[ARM]** アーキテクチャ、ターゲットとして **[デバイス]** を選択して、HoloLens 2 用に Visual Studio を構成します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-216">Configure Visual Studio for HoloLens 2 by selecting the **Master** or **Release** configuration, the **ARM** architecture, and **Device** as target:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

<span data-ttu-id="ec90f-218">HoloLens 2 をコンピューターに接続します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-218">Connect your HoloLens 2 to your computer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec90f-219">デバイスに対してビルドする前に、デバイスが開発者モードになっており、かつ、開発コンピューターとペアリングされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec90f-219">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="ec90f-220">この両方のステップを完了するには、[こちらの手順](using-visual-studio.md)に従います。</span><span class="sxs-lookup"><span data-stu-id="ec90f-220">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

<span data-ttu-id="ec90f-221">最後の手順として、 **[デバッグ]**  >  **[デバッグなしで開始]** を選択してビルドし、デバイスにデプロイします。</span><span class="sxs-lookup"><span data-stu-id="ec90f-221">The final step is to build and deploy to your device by selecting **Debug** > **Start Without Debugging**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

<span data-ttu-id="ec90f-223">これらの手順では、HoloLens 2 デバイスに配置することを前提としていますが、[HoloLens 2 エミュレーター](using-the-hololens-emulator.md)に配置することも、[サイドローディング用のアプリ パッケージ](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ec90f-223">While these instructions assume you will be deploying to a HoloLens 2 device, you can also deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span></span>

<span data-ttu-id="ec90f-224">[デバッグなしで開始] を選択すると、ビルドが成功した時点でアプリケーションがデバイス上ですぐに起動しますが、デバッガーがアタッチされていない状態であり、Visual Studio にデバッグ情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="ec90f-224">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="ec90f-225">これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-225">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

<span data-ttu-id="ec90f-226">アプリケーションを自動的に起動せずにデバイスに配置するには、[ビルド] > [ソリューションの配置] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-226">To deploy to your device without having the application start automatically, you can select Build > Deploy Solution.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ec90f-227">結論</span><span class="sxs-lookup"><span data-stu-id="ec90f-227">Congratulations</span></span>

<!-- TODO: Consider cleanup and adding in app screenshots -->
<span data-ttu-id="ec90f-228">これで、最初の HoloLens 2 アプリケーションがデプロイされました。</span><span class="sxs-lookup"><span data-stu-id="ec90f-228">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="ec90f-229">手順に従うと、HoloLens 2 によって認識されたすべてのサーフェイスに対応する空間マッピングのメッシュが表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="ec90f-229">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="ec90f-230">さらに、ハンド トラッキング用の手および指に対するインジケーターと、アプリケーションのパフォーマンスを監視するためのフレーム レート カウンターも表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="ec90f-230">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="ec90f-231">これらは、Mixed Reality ツールキットに含まれている、すぐに使用できる基礎となる部分のほんの一部です。</span><span class="sxs-lookup"><span data-stu-id="ec90f-231">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="ec90f-232">以降のチュートリアルでは、HoloLens 2 と Mixed Reality ツールキットの機能を十分に探索できるように、シーンにコンテンツや対話機能を追加する作業を開始します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-232">In the tutorials to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="ec90f-233">アプリでは、診断プロファイラーに気付くことがあります。この表示を切り替えるには、音声コマンド **Toogle Diagnostics** を使用します。</span><span class="sxs-lookup"><span data-stu-id="ec90f-233">In the app, you may notice the Diagnostics profiler, you can toggle it's visibility using the speech command **Toogle Diagnostics**.</span></span> <span data-ttu-id="ec90f-234">ただし、一般に、アプリに対する変更がパフォーマンスに影響を与える可能性がある場合を把握するために、開発中に常にプロファイラーを表示したままにしておくことをお勧めします。たとえば、HoloLens 2 アプリケーションは [60 FPSで継続的に実行](understanding-performance-for-mixed-reality.md)される必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec90f-234">However, it is generally recommended to keep the profiler visible at all times during development to understand when changes to the app may have impacted performance, for example, HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="ec90f-235">次のチュートリアル:3.ユーザー インターフェイスの作成と Mixed Reality ツールキットの構成</span><span class="sxs-lookup"><span data-stu-id="ec90f-235">Next Tutorial: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)
