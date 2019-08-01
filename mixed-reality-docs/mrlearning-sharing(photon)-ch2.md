---
title: 複数ユーザー機能のチュートリアル-2. Unity を開発用に準備する
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 9d42811157db108baad51eab3f367a06a11b7f7b
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701976"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="6f86e-105">2. Unity を開発用に準備する</span><span class="sxs-lookup"><span data-stu-id="6f86e-105">2. Getting Unity ready for development</span></span> 


<span data-ttu-id="6f86e-106">このチュートリアルでは、Mixed Reality Toolkit のインポート、ビルド設定の構成、シーンの準備など、アプリケーション開発のために Unity を準備して構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6f86e-106">In this tutorial, we learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="6f86e-107">目的</span><span class="sxs-lookup"><span data-stu-id="6f86e-107">Objectives</span></span>

- <span data-ttu-id="6f86e-108">アプリケーション開発のための Unity の構成</span><span class="sxs-lookup"><span data-stu-id="6f86e-108">Configure Unity for application development</span></span>

- <span data-ttu-id="6f86e-109">Mixed Reality ツールキットをインポートする</span><span class="sxs-lookup"><span data-stu-id="6f86e-109">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="6f86e-110">プロジェクトシーンを準備する</span><span class="sxs-lookup"><span data-stu-id="6f86e-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="6f86e-111">手順</span><span class="sxs-lookup"><span data-stu-id="6f86e-111">Instructions</span></span>

1. <span data-ttu-id="6f86e-112">ここをクリックして、Mixed Reality Toolkit unity パッケージをダウンロードして保存し[ます。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="6f86e-112">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>

2. <span data-ttu-id="6f86e-113">Unity で、[アセット] メニューをクリックし、[パッケージのインポート] をクリックして、[カスタムパッケージ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f86e-113">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="6f86e-115">手順 1. で指定したリンクからダウンロードした Unity パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="6f86e-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="6f86e-116">[インポート] ポップアップウィンドウが Unity に表示されたら、[インポート] ボタンをクリックしてインポートを開始します。</span><span class="sxs-lookup"><span data-stu-id="6f86e-116">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="6f86e-117">MRTK のインポートには数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6f86e-117">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="6f86e-119">注:ダウンロードしたパッケージは、ファイルを保存したローカルフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="6f86e-119">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="6f86e-120">上の図では、パッケージを検索する場所はされるません。</span><span class="sxs-lookup"><span data-stu-id="6f86e-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="6f86e-121">新しいシーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="6f86e-121">Create a new scene.</span></span> <span data-ttu-id="6f86e-122">これを行うには、[ファイル] をクリックし、[新しいシーン] を選択します)。</span><span class="sxs-lookup"><span data-stu-id="6f86e-122">This can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="6f86e-123">シーンを HLSharedProjectMain として保存します。</span><span class="sxs-lookup"><span data-stu-id="6f86e-123">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="6f86e-124">注: 次の図のようなポップアップが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="6f86e-124">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="6f86e-125">ここでは、[いいえ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f86e-125">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="6f86e-127">Mixed Reality Toolkit の [シーンに追加] をクリックし、[構成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f86e-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="6f86e-129">この処理が完了すると、新しい構成ファイルが表示され、プロファイルをカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="6f86e-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="6f86e-130">[コピーとカスタマイズ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f86e-130">Click Copy and Customize.</span></span>

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="6f86e-134">[診断] ウィンドウを非表示にする場合は、下にスクロールし、[診断システムを有効にする] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="6f86e-134">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="6f86e-135">アプリケーションの開発中に、パフォーマンスを監視し、運用またはアプリケーションのデモンストレーション中に無効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6f86e-135">We recommend keeping the diagnostics window enabled during application development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="6f86e-137">Ctrl + shift + B キーを押すか、[ファイル > ビルド設定] に移動して、ビルド設定を開きます。</span><span class="sxs-lookup"><span data-stu-id="6f86e-137">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="6f86e-138">プログラムは、現在 PC、Mac、および Linux スタンドアロンプラットフォームで設定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6f86e-138">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="6f86e-139">HoloLens 2 開発の場合は、プラットフォームをユニバーサル Windows プラットフォームに設定します。</span><span class="sxs-lookup"><span data-stu-id="6f86e-139">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="6f86e-140">それを選択し、[プラットフォームの切り替え] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f86e-140">Select it and click Switch Platform.</span></span>

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="6f86e-142">完了したら、[Open シーンの追加] というボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f86e-142">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="6f86e-143">次に、[インスペクター] パネルにアクセスし、[サポートされている仮想現実 (下の図を参照)] の右側にあるチェックボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6f86e-143">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="6f86e-144">また、次の図に示すように、[シーン/HLSharedProjectMain] の横のチェックボックスもオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6f86e-144">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="6f86e-146">[インスペクター] パネルの [発行の設定] セクションで、[機能] まで下にスクロールし、次のチェックボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6f86e-146">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="6f86e-148">ここでダウンロードできる SharingAssetCollection というカスタムパッケージをインポートし[ます。](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span><span class="sxs-lookup"><span data-stu-id="6f86e-148">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span></span>

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. <span data-ttu-id="6f86e-150">[プロジェクト] パネルで、Prefabs フォルダーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="6f86e-150">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="6f86e-151">次のいくつかの手順では、いくつかの prefabs をシーンに実装します。</span><span class="sxs-lookup"><span data-stu-id="6f86e-151">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="6f86e-152">Prefabs フォルダーで、[prefab]、[デバッグ] ウィンドウをクリックし、階層にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="6f86e-152">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="6f86e-153">完了したら、[ファイル] をクリックし、[保存] をクリックしてプロジェクトを保存するか、ctrl + S キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6f86e-153">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="6f86e-155">注:Prefab をクリックするとポップアップが表示され、TMP Essentials について質問されることがあります。</span><span class="sxs-lookup"><span data-stu-id="6f86e-155">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="6f86e-156">必要に応じて、[TMP Essentials のインポート] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f86e-156">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="6f86e-157">このポップアップが表示された場合は、テキスト関連のエラーが発生しないように、階層から prefab を削除し、階層に再ドラッグする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="6f86e-157">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="6f86e-159">結論</span><span class="sxs-lookup"><span data-stu-id="6f86e-159">Congratulations</span></span>

<span data-ttu-id="6f86e-160">Unity プロジェクトは Photon の準備ができました。</span><span class="sxs-lookup"><span data-stu-id="6f86e-160">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="6f86e-161">今後のチュートリアルでは、このシーンと Unity プロジェクトを完全な共有エクスペリエンスに向けて構築します。</span><span class="sxs-lookup"><span data-stu-id="6f86e-161">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="6f86e-162">[次のチュートリアル:3.複数ユーザーの接続](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="6f86e-162">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

