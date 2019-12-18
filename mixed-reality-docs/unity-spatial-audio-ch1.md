---
title: 空間オーディオのチュートリアル-1. プロジェクトへの空間オーディオの追加
description: Microsoft Spatializer プラグインを Unity プロジェクトに追加して、HoloLens 2 HRTF ハードウェアオフロードにアクセスします。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ
ms.openlocfilehash: 8978017b3ce6c49a81b3eee2fe21e9234f4e71f0
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182799"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="4e408-105">Unity プロジェクトへの空間オーディオの追加</span><span class="sxs-lookup"><span data-stu-id="4e408-105">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="4e408-106">HoloLens2 の空間オーディオ tutioral for Unity へようこそ。</span><span class="sxs-lookup"><span data-stu-id="4e408-106">Welcome to the spatial audio tutioral for Unity on HoloLens2.</span></span> <span data-ttu-id="4e408-107">このチュートリアルでは、次の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="4e408-107">This tutorial sequence shows:</span></span>
* <span data-ttu-id="4e408-108">Unity の HoloLens 2 で HRTF offload を使用する方法</span><span class="sxs-lookup"><span data-stu-id="4e408-108">How to use HRTF offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="4e408-109">HRTF オフロードを使用するときにリバーブを有効にする方法</span><span class="sxs-lookup"><span data-stu-id="4e408-109">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="4e408-110">[Microsoft Spatializer GitHub リポジトリ](https://github.com/microsoft/spatialaudio-unity)には、このチュートリアルシーケンスの完成した Unity プロジェクトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4e408-110">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="4e408-111">サウンドの spatialize に役立つ場合の推奨事項については、「[空間サウンドの設計](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e408-111">For our recommendations on when it can be helpful to spatialize sounds, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="objectives"></a><span data-ttu-id="4e408-112">目標</span><span class="sxs-lookup"><span data-stu-id="4e408-112">Objectives</span></span>
<span data-ttu-id="4e408-113">この最初の章では、次のことについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4e408-113">In this first chapter, you'll:</span></span>
* <span data-ttu-id="4e408-114">Unity プロジェクトを作成して MRTK をインポートする</span><span class="sxs-lookup"><span data-stu-id="4e408-114">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="4e408-115">Microsoft spatializer プラグインをインポートする</span><span class="sxs-lookup"><span data-stu-id="4e408-115">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="4e408-116">Microsoft spatializer プラグインを有効にする</span><span class="sxs-lookup"><span data-stu-id="4e408-116">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="4e408-117">開発者ワークステーションで空間オーディオを有効にする</span><span class="sxs-lookup"><span data-stu-id="4e408-117">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="4e408-118">プロジェクトを作成し、Unity の NuGet を追加する</span><span class="sxs-lookup"><span data-stu-id="4e408-118">Create a project and add NuGet for Unity</span></span>
<span data-ttu-id="4e408-119">空の Unity プロジェクトから開始し、Unity 用に NuGet を追加して構成します。</span><span class="sxs-lookup"><span data-stu-id="4e408-119">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="4e408-120">最新の NuGetForUnity をダウンロードし[ます。 unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="4e408-120">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="4e408-121">Unity のメニューバーで、 **[資産-> インポートパッケージ-> カスタムパッケージ]** をクリックし、NuGetForUnity パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4e408-121">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![カスタムパッケージのインポート](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="4e408-123">Windows Mixed Reality パッケージを追加する</span><span class="sxs-lookup"><span data-stu-id="4e408-123">Add the Windows Mixed Reality package</span></span>
<span data-ttu-id="4e408-124">Unity 2019 以降での Windows Mixed Reality のサポートは、オプションのパッケージに含まれています。</span><span class="sxs-lookup"><span data-stu-id="4e408-124">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="4e408-125">プロジェクトに追加するには、Unity のメニューバーから [ **Window-> Package Manager]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="4e408-125">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![パッケージマネージャーメニュー](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="4e408-127">次に、 **Windows Mixed Reality**パッケージを検索してインストールします。</span><span class="sxs-lookup"><span data-stu-id="4e408-127">Then find and install the **Windows Mixed Reality** package:</span></span>

![パッケージマネージャーウィンドウ](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="4e408-129">MRTK と Microsoft Spatializer をインストールする</span><span class="sxs-lookup"><span data-stu-id="4e408-129">Install MRTK and Microsoft Spatializer</span></span>
<span data-ttu-id="4e408-130">Unity 用の NuGet を使用して、MRTK と Microsoft Spatializer プラグインをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4e408-130">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="4e408-131">Unity のメニューバーで、[ **nuget->] [Nuget パッケージの管理**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e408-131">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![NuGet パッケージの管理](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="4e408-133">**検索**ボックスに「MixedReality」と入力し、MRTK コアパッケージ ( **MixedReality** ) をインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="4e408-133">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![MRTK NuGet パッケージ](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="4e408-135">[Mrtk NuGet パッケージ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html)には、追加のコンテキストと詳細があります。</span><span class="sxs-lookup"><span data-stu-id="4e408-135">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="4e408-136">**検索**ボックスに「SpatialAudio」と入力し、microsoft Spatializer パッケージ: **SpatialAudio**をインストールします。</span><span class="sxs-lookup"><span data-stu-id="4e408-136">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![Spatializer プラグイン NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="4e408-138">プロジェクトでの MRTK の設定</span><span class="sxs-lookup"><span data-stu-id="4e408-138">Set up MRTK in your project</span></span>

1. <span data-ttu-id="4e408-139">ビルドの設定 ウィンドウを開き、**ファイル > ビルドの設定** に移動します。</span><span class="sxs-lookup"><span data-stu-id="4e408-139">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="4e408-140">_ユニバーサル Windows プラットフォーム_を選択し、 **[プラットフォームの切り替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e408-140">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="4e408-141">[**ビルド] ウィンドウ**の **[プレーヤーの設定]** をクリックして、 **[インスペクター]** ウィンドウの **[プレーヤーの設定]** プロパティを開きます。</span><span class="sxs-lookup"><span data-stu-id="4e408-141">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="4e408-142">**[XR の設定]** で、 **[Virtual Reality がサポート]** する チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4e408-142">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="4e408-143">**[XR の設定]** で、**ステレオレンダリングモード**を**シングルパスインスタンス**化に変更します。</span><span class="sxs-lookup"><span data-stu-id="4e408-143">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="4e408-144">**[発行の設定]** で、 **[機能]** セクションの **[空間の認識]** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4e408-144">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="4e408-145">メニューバーで  **Mixed Reality Toolkit-> シーンに追加 を**クリックし、構成 をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e408-145">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="4e408-146">を使用して、シーンに MRTK を追加します。</span><span class="sxs-lookup"><span data-stu-id="4e408-146">to add MRTK to your scene.</span></span>

<span data-ttu-id="4e408-147">アプリをビルドして HoloLens 2 にデプロイする方法など、その他のガイダンスについては、 [MR ラーニングベースモジュールの第1章](mrlearning-base-ch1.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e408-147">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="4e408-148">Microsoft Spatializer プラグインを有効にする</span><span class="sxs-lookup"><span data-stu-id="4e408-148">Enable the Microsoft Spatializer plugin</span></span>
<span data-ttu-id="4e408-149">**Microsoft Spatializer**プラグインを有効にします。</span><span class="sxs-lookup"><span data-stu-id="4e408-149">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="4e408-150">**[編集-> プロジェクトの設定-> オーディオ]** を開き、 **Spatializer プラグイン**を "Microsoft Spatializer" に変更します。</span><span class="sxs-lookup"><span data-stu-id="4e408-150">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="4e408-151">**プロジェクト設定**の**Audio**セクションは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4e408-151">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Spatializer プラグインを表示するプロジェクト設定](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="4e408-153">ワークステーションで空間オーディオを有効にする</span><span class="sxs-lookup"><span data-stu-id="4e408-153">Enable spatial audio on your workstation</span></span>
<span data-ttu-id="4e408-154">Windows のデスクトップバージョンでは、空間オーディオは既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="4e408-154">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="4e408-155">これを有効にするには、タスクバーのボリュームアイコンを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="4e408-155">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="4e408-156">HoloLens 2 で耳になる内容を最大限に活用するには、 **[空間サウンド > Windows Sonic For ヘッドホン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4e408-156">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![デスクトップ空間オーディオの設定](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="4e408-158">この設定は、Unity エディターでプロジェクトをテストする場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="4e408-158">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4e408-159">次のステップ</span><span class="sxs-lookup"><span data-stu-id="4e408-159">Next steps</span></span>
<span data-ttu-id="4e408-160">[Unity の空間オーディオ chapter 2](unity-spatial-audio-ch2.md) to spatialize button 対話サウンドに進みます。</span><span class="sxs-lookup"><span data-stu-id="4e408-160">Continue on to [Unity spatial audio chapter 2](unity-spatial-audio-ch2.md) to spatialize button interaction sounds.</span></span>

