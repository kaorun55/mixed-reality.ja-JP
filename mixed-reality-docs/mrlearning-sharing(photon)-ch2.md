---
title: 複数ユーザー機能のチュートリアル-2. Unity を開発用に準備する
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 750161ff4c52a7ab71869b3cb0f97197d4ad09f2
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2019
ms.locfileid: "74106045"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="ca0bd-105">2. Unity を開発用に準備する</span><span class="sxs-lookup"><span data-stu-id="ca0bd-105">2. Getting Unity ready for development</span></span> 


<span data-ttu-id="ca0bd-106">このチュートリアルでは、Mixed Reality Toolkit のインポート、ビルド設定の構成、シーンの準備など、アプリケーション開発のために Unity を準備して構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="ca0bd-107">目標</span><span class="sxs-lookup"><span data-stu-id="ca0bd-107">Objectives</span></span>

- <span data-ttu-id="ca0bd-108">アプリケーション開発のための Unity の構成</span><span class="sxs-lookup"><span data-stu-id="ca0bd-108">Configure Unity for application development</span></span>

- <span data-ttu-id="ca0bd-109">Mixed Reality ツールキットをインポートする</span><span class="sxs-lookup"><span data-stu-id="ca0bd-109">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="ca0bd-110">プロジェクトシーンを準備する</span><span class="sxs-lookup"><span data-stu-id="ca0bd-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="ca0bd-111">手順</span><span class="sxs-lookup"><span data-stu-id="ca0bd-111">Instructions</span></span>

1. <span data-ttu-id="ca0bd-112">ここをクリックして、Mixed Reality Toolkit Foundation unity パッケージをダウンロードして保存し[ます。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="ca0bd-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span></span>

2. <span data-ttu-id="ca0bd-113">Unity で、[アセット] メニューをクリックし、[パッケージのインポート] をクリックして、[カスタムパッケージ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="ca0bd-115">手順 1. で指定したリンクからダウンロードした Unity パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="ca0bd-116">[インポート] ポップアップウィンドウが Unity に表示されたら、[インポート] ボタンをクリックして MRTK のインポートを開始します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="ca0bd-117">この処理には数分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-117">This may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="ca0bd-119">メモ: ダウンロードしたパッケージは、ファイルを保存したローカルフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-119">Note: The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="ca0bd-120">上の図では、パッケージを検索する場所はされるません。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="ca0bd-121">新しいシーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-121">Create a new scene.</span></span> <span data-ttu-id="ca0bd-122">これを行うには、[ファイル] をクリックし、[新しいシーン] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-122">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="ca0bd-123">HLSharedProjectMain として保存します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-123">Save it as HLSharedProjectMain.</span></span>

> <span data-ttu-id="ca0bd-124">注: 次の図のようなポップアップが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-124">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="ca0bd-125">ここでは、[いいえ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-125">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="ca0bd-127">Mixed Reality Toolkit の [シーンに追加] をクリックし、[構成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="ca0bd-129">この処理が完了すると、新しい構成ファイルが表示され、プロファイルをカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> 

![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. <span data-ttu-id="ca0bd-131">階層から [Mixed-Reality Toolkit (MRTK)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-131">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="ca0bd-132">[インスペクター] パネルで、Mixed Reality Toolkit スクリプトを探して、次の図に示すように [Copy & Customize] ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-132">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="ca0bd-133">この後、ポップアップメニューの [複製] オプションを選択すると、pop が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-133">A pop will appear after this and select clone option in the pop up menu.</span></span>

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

7. <span data-ttu-id="ca0bd-136">[診断] ウィンドウを非表示にする場合は、下にスクロールし、[診断システムを有効にする] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-136">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="ca0bd-137">アプリケーションの開発中は、パフォーマンスを監視し、運用またはアプリケーションのデモンストレーション中に無効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-137">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="ca0bd-139">Ctrl + shift + B キーを押すか、[ファイル > ビルド設定] に移動して、ビルド設定を開きます。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-139">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="ca0bd-140">プログラムは、現在 PC、Mac、および Linux スタンドアロンプラットフォームで設定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-140">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="ca0bd-141">HoloLens 2 開発の場合は、プラットフォームをユニバーサル Windows プラットフォームに設定します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-141">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="ca0bd-142">それを選択し、[プラットフォームの切り替え] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-142">Select it and click Switch Platform.</span></span>

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="ca0bd-144">完了したら、[Open シーンの追加] というボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-144">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="ca0bd-145">次に、[インスペクター] パネルにアクセスし、[サポートされている仮想現実 (下の図を参照)] の右側にあるチェックボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-145">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="ca0bd-146">また、次の図に示すように、[シーン/HLSharedProjectMain] の横のチェックボックスもオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-146">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="ca0bd-148">[インスペクター] パネルの [発行の設定] セクションで、[機能] まで下にスクロールし、次のチェックボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-148">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="ca0bd-150">一覧表示されたカスタムパッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-150">Import the listed custom packages:</span></span>

    <span data-ttu-id="ca0bd-151">」を参照します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-151">a.</span></span> [<span data-ttu-id="ca0bd-152">HoloLens2. 2.1.0.0. unitypackage を実行します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-152">Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

    <span data-ttu-id="ca0bd-153">b.</span><span class="sxs-lookup"><span data-stu-id="ca0bd-153">b.</span></span> [<span data-ttu-id="ca0bd-154">Unity. HoloLens2. 2.1.0.0. unitypackage を行います。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-154">Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.0/Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage)

    >[!TIP]
    ><span data-ttu-id="ca0bd-155">「[チュートリアル](mrlearning-base-ch1.md)入門」を完了している場合でも、 _HoloLens2_という名前の unity パッケージがコンピューターに保存されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-155">If you have completed the [Getting started tutorials](mrlearning-base-ch1.md), you might still have the Unity package named _Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage_ stored on your computer.</span></span> <span data-ttu-id="ca0bd-156">その場合は、上記の手順に記載されている資産のダウンロードをスキップできます。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-156">If so, you can skip downloading the asset listed in step a above.</span></span>

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. <span data-ttu-id="ca0bd-158">[プロジェクト] パネルで、Prefabs フォルダーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-158">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="ca0bd-159">次の手順では、いくつかの prefabs をシーンに実装します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-159">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="ca0bd-160">Prefabs フォルダーで、[prefab]、[デバッグ] ウィンドウをクリックし、階層にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-160">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="ca0bd-161">完了したら、[ファイル] をクリックし、[保存] をクリックしてプロジェクトを保存するか、ctrl + S キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-161">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="ca0bd-163">注: prefab をクリックするとポップアップが表示され、TMP Essentials について質問されることがあります。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-163">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="ca0bd-164">必要に応じて、[TMP Essentials のインポート] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-164">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="ca0bd-165">このポップアップが表示された場合は、テキスト関連のエラーが発生しないように、階層から prefab を削除し、階層に再ドラッグする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-165">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="ca0bd-167">結論</span><span class="sxs-lookup"><span data-stu-id="ca0bd-167">Congratulations</span></span>

<span data-ttu-id="ca0bd-168">Unity プロジェクトは Photon の準備ができました。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-168">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="ca0bd-169">今後のチュートリアルでは、このシーンと Unity プロジェクトを完全な共有エクスペリエンスに向けて構築します。</span><span class="sxs-lookup"><span data-stu-id="ca0bd-169">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="ca0bd-170">[次のチュートリアル: 3. 複数のユーザーを接続する](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="ca0bd-170">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

