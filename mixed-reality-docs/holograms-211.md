---
title: MR 入力 211 のジェスチャ
description: ジェスチャの概念の詳細については、Unity、Visual Studio は、HoloLens を使用してこのコーディング チュートリアルに従ってください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit unity、academy、チュートリアルでは、ジェスチャ
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603386"
---
>[!NOTE]
><span data-ttu-id="51a3b-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="51a3b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="51a3b-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="51a3b-106">これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="51a3b-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="51a3b-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="51a3b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="51a3b-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="51a3b-110">MR 入力 211:ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="51a3b-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="51a3b-111">[ジェスチャ](gestures.md)をアクションにユーザーの意図を変換します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="51a3b-112">ジェスチャでは、ユーザーはホログラムと対話できます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="51a3b-113">このコースでユーザーの手を追跡、ユーザーの入力に応答する方法について説明し、ユーザーに与えるフィードバック ベースの一方で状態と位置。</span><span class="sxs-lookup"><span data-stu-id="51a3b-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="51a3b-114">[MR 基本 101](holograms-101.md)、単純なエア タップ ジェスチャを使用して、ホログラムと対話します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="51a3b-115">ここで、エア タップのジェスチャだけにとどまらないし、新しい概念を検証します。、</span><span class="sxs-lookup"><span data-stu-id="51a3b-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="51a3b-116">ユーザーの手が追跡されていることを検出し、ユーザーにフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="51a3b-117">ホログラムを回転するのにには、ナビゲーションのジェスチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="51a3b-118">ユーザーの手がビューの外に出るときに、フィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="51a3b-119">操作イベントを使用して、自分の手でホログラムを移動します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="51a3b-120">このコースで Unity プロジェクトを再度**モデル エクスプ ローラー**に組み込まれています[MR 入力 210](holograms-210.md)します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="51a3b-121">「宇宙飛行士友人は、これら新しいジェスチャ概念のところ役立ちますに戻っています。</span><span class="sxs-lookup"><span data-stu-id="51a3b-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="51a3b-122">以前のバージョンの Unity と Mixed Reality Toolkit を使用して、以下の各章に埋め込まれたビデオが記録されています。</span><span class="sxs-lookup"><span data-stu-id="51a3b-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="51a3b-123">詳細な手順については、正確かつ最新ですが、スクリプトとは、無効な対応するビデオの中でビジュアルを表示があります。</span><span class="sxs-lookup"><span data-stu-id="51a3b-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="51a3b-124">ビデオでは、後生のために含まれる保持され、概念説明のため、引き続き適用されます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="51a3b-125">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="51a3b-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="51a3b-126">コース</span><span class="sxs-lookup"><span data-stu-id="51a3b-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="51a3b-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="51a3b-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="51a3b-128"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="51a3b-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="51a3b-129">MR 入力 211:ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="51a3b-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="51a3b-130">✔️</span><span class="sxs-lookup"><span data-stu-id="51a3b-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="51a3b-131">✔️</span><span class="sxs-lookup"><span data-stu-id="51a3b-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="51a3b-132">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="51a3b-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="51a3b-133">前提条件</span><span class="sxs-lookup"><span data-stu-id="51a3b-133">Prerequisites</span></span>

* <span data-ttu-id="51a3b-134">正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="51a3b-135">基本的なC#プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="51a3b-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="51a3b-136">完了する必要があります[MR 基本 101](holograms-101.md)します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="51a3b-137">完了する必要があります[MR 入力 210](holograms-210.md)します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="51a3b-138">HoloLens デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="51a3b-139">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="51a3b-139">Project files</span></span>

* <span data-ttu-id="51a3b-140">ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip)プロジェクトに必要です。</span><span class="sxs-lookup"><span data-stu-id="51a3b-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="51a3b-141"> Unity 2017.2 またはそれ以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="51a3b-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="51a3b-142">解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。</span><span class="sxs-lookup"><span data-stu-id="51a3b-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="51a3b-143">をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="51a3b-144">正誤表と注意事項</span><span class="sxs-lookup"><span data-stu-id="51a3b-144">Errata and Notes</span></span>

* <span data-ttu-id="51a3b-145">「マイ コードのみを有効にする」無効にする必要があります (*unchecked*) -> ツールの Visual Studio でのオプションには、デバッグ、コードにブレークポイントをヒットするには-> です。</span><span class="sxs-lookup"><span data-stu-id="51a3b-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="51a3b-146">0 - Unity のセットアップ」の章</span><span class="sxs-lookup"><span data-stu-id="51a3b-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="51a3b-147">手順</span><span class="sxs-lookup"><span data-stu-id="51a3b-147">Instructions</span></span>

1. <span data-ttu-id="51a3b-148">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-148">Start Unity.</span></span>
2. <span data-ttu-id="51a3b-149">**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-149">Select **Open**.</span></span>
3. <span data-ttu-id="51a3b-150">移動し、**ジェスチャ**フォルダー以前されていないアーカイブします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="51a3b-151">検索し、選択、**開始**/**モデル エクスプ ローラー**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="51a3b-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="51a3b-152">をクリックして、**フォルダーの選択**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="51a3b-153">**プロジェクト**パネルで、展開、**シーン**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="51a3b-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="51a3b-154">ダブルクリック**ModelExplorer**シーン Unity で読み込めません。</span><span class="sxs-lookup"><span data-stu-id="51a3b-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="51a3b-155">ビルド</span><span class="sxs-lookup"><span data-stu-id="51a3b-155">Building</span></span>

1. <span data-ttu-id="51a3b-156">Unity では、次のように選択します。**ファイル > Build Settings**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="51a3b-157">場合**シーン/ModelExplorer**に記載されていない**Scenes In Build**、 をクリックして**開くシーンを追加**シーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="51a3b-158">具体的には、HoloLens の開発中、設定**ターゲット デバイス**に**HoloLens**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="51a3b-159">それ以外の場合、残して**任意のデバイス**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="51a3b-160">確認**ビルド タイプ**に設定されている**D3D**と**SDK**に設定されている**インストールされている最新**(16299 またはそれ以降の SDK がある必要があります)。</span><span class="sxs-lookup"><span data-stu-id="51a3b-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="51a3b-161">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-161">Click **Build**.</span></span>
6. <span data-ttu-id="51a3b-162">作成、**新しいフォルダー** "App"という名前です。</span><span class="sxs-lookup"><span data-stu-id="51a3b-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="51a3b-163">1 回のクリック、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="51a3b-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="51a3b-164">キーを押して**フォルダーの選択**Unity は Visual Studio のプロジェクトのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="51a3b-165">Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="51a3b-166">開く、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="51a3b-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="51a3b-167">開く、 **ModelExplorer Visual Studio ソリューション**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="51a3b-168">HoloLens へのデプロイ: 場合</span><span class="sxs-lookup"><span data-stu-id="51a3b-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="51a3b-169">デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x86**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="51a3b-170">ローカル コンピューター] ボタンの横の矢印のドロップダウンをクリックし、[**リモート マシン**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="51a3b-171">入力**HoloLens デバイスの IP アドレス**認証モードを設定および**ユニバーサル (暗号化されていないプロトコル)** します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="51a3b-172">クリックして**選択**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-172">Click **Select**.</span></span> <span data-ttu-id="51a3b-173">デバイスの IP アドレスがわからない場合に参照**設定 > ネットワークとインターネット > 詳細オプション**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="51a3b-174">上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="51a3b-175">最初に、デバイスに展開するには、する必要があります[Visual Studio をペアリング](using-visual-studio.md#pairing-your-device-hololens)します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="51a3b-176">アプリが展開されると、消去、 **Fitbox**で、**ジェスチャ を選択**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="51a3b-177">場合は、イマーシブ ヘッドセットへのデプロイ。</span><span class="sxs-lookup"><span data-stu-id="51a3b-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="51a3b-178">デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x64**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="51a3b-179">必ず、配置ターゲットに設定されて**ローカル マシン**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="51a3b-180">上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="51a3b-181">アプリが展開されると、消去、 **Fitbox**アニメーション コント ローラーで、トリガーを取得することによって。</span><span class="sxs-lookup"><span data-stu-id="51a3b-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="51a3b-182">Visual Studio でエラー パネルの赤いエラーの一部が分かります。</span><span class="sxs-lookup"><span data-stu-id="51a3b-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="51a3b-183">それらを無視しても安全になります。</span><span class="sxs-lookup"><span data-stu-id="51a3b-183">It is safe to ignore them.</span></span> <span data-ttu-id="51a3b-184">ビルドの進行状況を実際に表示する出力パネルへの切り替え。</span><span class="sxs-lookup"><span data-stu-id="51a3b-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="51a3b-185">エラー出力 パネルにでは修正プログラム (ほとんどの多くの場合、スクリプトで間違いに起因) を作成することが必要です。</span><span class="sxs-lookup"><span data-stu-id="51a3b-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="51a3b-186">第 1 章 - 手の形にフィードバックが検出されました</span><span class="sxs-lookup"><span data-stu-id="51a3b-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="51a3b-187">目標</span><span class="sxs-lookup"><span data-stu-id="51a3b-187">Objectives</span></span>

* <span data-ttu-id="51a3b-188">追跡イベントを渡すためにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="51a3b-189">手の形が追跡されているときにユーザーを表示するのにには、カーソルのフィードバックを使用します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

### <a name="instructions"></a><span data-ttu-id="51a3b-190">手順</span><span class="sxs-lookup"><span data-stu-id="51a3b-190">Instructions</span></span>

* <span data-ttu-id="51a3b-191">**階層**パネルで、展開、 **InputManager**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="51a3b-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="51a3b-192">探し、選択、 **GesturesInput**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="51a3b-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="51a3b-193">**InteractionInputSource.cs**スクリプトは、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="51a3b-194">InteractionSourceDetected と InteractionSourceLost イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="51a3b-195">HandDetected 状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="51a3b-196">InteractionSourceDetected と InteractionSourceLost イベントからアンサブスク ライブします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="51a3b-197">次に、アップグレード、カーソルから[MR 入力 210](holograms-210.md)フィードバックによって、ユーザーのアクションを示す 1 つにします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="51a3b-198">**階層**パネルで、**カーソル**オブジェクトし、それを削除します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="51a3b-199">**プロジェクト**パネルで、検索**CursorWithFeedback**までドラッグし、**階層**パネル。</span><span class="sxs-lookup"><span data-stu-id="51a3b-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="51a3b-200">をクリックして**InputManager**で、**階層**をドラッグして、パネル、 **CursorWithFeedback**オブジェクトから、**階層**に、InputManager の**SimpleSinglePointerSelector**の**カーソル**フィールドでは、下部にある、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="51a3b-201">をクリックして、 **CursorWithFeedback**で、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="51a3b-202">**インスペクター**パネルで、展開**カーソル状態データ**上、**オブジェクト カーソル**スクリプト。</span><span class="sxs-lookup"><span data-stu-id="51a3b-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="51a3b-203">**カーソル状態データ**これと同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="51a3b-204">すべて**監視**状態の意味は手が検出されなかった場合、ユーザーを探し、単にします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="51a3b-205">すべて**Interact**状態では、手動またはコント ローラーが検出されたことを意味します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="51a3b-206">すべて**ホバー**状態の意味は、ユーザーはホログラム見る。</span><span class="sxs-lookup"><span data-stu-id="51a3b-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="51a3b-207">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="51a3b-207">Build and Deploy</span></span>

* <span data-ttu-id="51a3b-208">Unity では、次のように使用します。**ファイル > Build Settings** 、アプリケーションをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="51a3b-209">開く、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="51a3b-209">Open the **App** folder.</span></span>
* <span data-ttu-id="51a3b-210">開くことがまだ開いていない場合、 **ModelExplorer Visual Studio ソリューション**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="51a3b-211">(既にビルド/展開して Visual Studio では、このプロジェクトのセットアップ中に場合、し、VS のインスタンスを開いて 'すべて再読み込み' が表示されたらクリックします)。</span><span class="sxs-lookup"><span data-stu-id="51a3b-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="51a3b-212">Visual Studio で、次のようにクリックします。**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="51a3b-213">アプリケーションのデプロイは、HoloLens 後、は、エア タップ ジェスチャを使用して fitbox を無視します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="51a3b-214">ビューに手を移動し、人差し指をハンドの追跡を開始する、空にします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="51a3b-215">自分の手を左に移動、右、上下します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="51a3b-216">手が検出され、ビューから失われたときに、カーソルがどのように変化するかをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="51a3b-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="51a3b-217">場合は、イマーシブ ヘッドセットの場合は、接続し、コント ローラーを切断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51a3b-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="51a3b-218">このフィードバックは、接続されているコント ローラーは常に使用できる""、没入型のデバイスでは、重要なになります。</span><span class="sxs-lookup"><span data-stu-id="51a3b-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="51a3b-219">第 2 章 - ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="51a3b-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="51a3b-220">目標</span><span class="sxs-lookup"><span data-stu-id="51a3b-220">Objectives</span></span>

* <span data-ttu-id="51a3b-221">「宇宙飛行士を回転するには、ナビゲーション ジェスチャ イベントをを使用します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="51a3b-222">手順</span><span class="sxs-lookup"><span data-stu-id="51a3b-222">Instructions</span></span>

<span data-ttu-id="51a3b-223">アプリケーションのナビゲーションのジェスチャを使用する編集するつもりは**GestureAction.cs**ナビゲーション ジェスチャが発生したときに、オブジェクトを回転します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="51a3b-224">さらに、ナビゲーションが使用可能なときに表示されるカーソルにフィードバックを追加します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="51a3b-225">**階層**パネルで、展開**CursorWithFeedback**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="51a3b-226">**ホログラム**フォルダー、検索、 **ScrollFeedback**資産。</span><span class="sxs-lookup"><span data-stu-id="51a3b-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="51a3b-227">ドラッグ アンド ドロップ、 **ScrollFeedback**にプレハブ、 **CursorWithFeedback**の GameObject、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="51a3b-228">をクリックして**CursorWithFeedback**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="51a3b-229">**インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="51a3b-230">メニューで、検索ボックスに入力**CursorFeedback**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="51a3b-231">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-231">Select the search result.</span></span>
7. <span data-ttu-id="51a3b-232">ドラッグ アンド ドロップ、 **ScrollFeedback**オブジェクトから、**階層**上に、**スクロール ゲーム オブジェクトの検出**プロパティ、**カーソル フィードバック**コンポーネント、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="51a3b-233">**階層**パネルで、 **AstroMan**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="51a3b-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="51a3b-234">**インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="51a3b-235">メニューで、検索ボックスに入力**ジェスチャによる操作**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="51a3b-236">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-236">Select the search result.</span></span>

<span data-ttu-id="51a3b-237">次に、 **GestureAction.cs** Visual Studio でします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="51a3b-238">コーディングの練習 2. c には、次のスクリプトを編集します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="51a3b-239">**回転、AstroMan**オブジェクトのナビゲーションのジェスチャを実行するたびにします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="51a3b-240">計算、 **rotationFactor**オブジェクトに適用する回転の量を制御します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="51a3b-241">**オブジェクトを回転させる**左または右に、ユーザーが、手の形を移動したときに、y 軸を中心。</span><span class="sxs-lookup"><span data-stu-id="51a3b-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="51a3b-242">2. c では、スクリプト、または置換下の完成したソリューションを使用してコードを実行する完全なコーディングします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

<span data-ttu-id="51a3b-243">いくつかの情報を使用して、その他のナビゲーション イベントが既に入力されて表示されます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="51a3b-244">ツールキットの上に GameObject プッシュ InputSystem のモーダル スタック、回転が始まった後に、「宇宙飛行士フォーカスを維持するために、ユーザーがないようにします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="51a3b-245">同様に、ジェスチャが完了すると、スタックからポップ GameObject ポップします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="51a3b-246">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="51a3b-246">Build and Deploy</span></span>

1. <span data-ttu-id="51a3b-247">Unity でアプリケーションをリビルドし、ビルドして、HoloLens で実行する Visual Studio からデプロイします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="51a3b-248">見つめます、飛行士カーソルの両側に 2 つの矢印が表示されます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="51a3b-249">この新しいビジュアルは、「宇宙飛行士を回転できることを示します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="51a3b-250">準備ができて位置 (インデックスの指が空を指して) に手を設定するため、HoloLens は手の追跡を開始します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="51a3b-251">回転するには、「宇宙飛行士をピンチ位置、人差し指を削減し、左または右 NavigationX ジェスチャをトリガーする、手の形を移動します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="51a3b-252">第 3 章 - 手の形のガイダンス</span><span class="sxs-lookup"><span data-stu-id="51a3b-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="51a3b-253">目標</span><span class="sxs-lookup"><span data-stu-id="51a3b-253">Objectives</span></span>

* <span data-ttu-id="51a3b-254">使用**ガイダンスのスコアを渡す**追跡手が失われる場合の予測をサポートします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="51a3b-255">提供**カーソル上でフィードバック**ときに、ユーザーの手の形に近いビューのカメラのエッジを表示します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="51a3b-256">手順</span><span class="sxs-lookup"><span data-stu-id="51a3b-256">Instructions</span></span>

1. <span data-ttu-id="51a3b-257">**階層**パネルで、 **CursorWithFeedback**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="51a3b-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="51a3b-258">**インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="51a3b-259">メニューで、検索ボックスに入力**手ガイダンス**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="51a3b-260">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-260">Select the search result.</span></span>
4. <span data-ttu-id="51a3b-261">**プロジェクト**パネル**ホログラム**フォルダー、検索、 **HandGuidanceFeedback**資産。</span><span class="sxs-lookup"><span data-stu-id="51a3b-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="51a3b-262">ドラッグ アンド ドロップ、 **HandGuidanceFeedback**上に資産、**手ガイダンス インジケーター**プロパティ、**インスペクター**パネル。</span><span class="sxs-lookup"><span data-stu-id="51a3b-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="51a3b-263">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="51a3b-263">Build and Deploy</span></span>

* <span data-ttu-id="51a3b-264">Unity でアプリケーションをリビルドし構築、HoloLens でアプリを体験する Visual Studio からデプロイします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="51a3b-265">手を表示し、追跡する際、人差し指を発生させます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="51a3b-266">ナビゲーションのジェスチャに「宇宙飛行士回転を開始 (インデックス指によるピンチ ジェスチャと一緒に thumb)。</span><span class="sxs-lookup"><span data-stu-id="51a3b-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="51a3b-267">実際には、左端、右端、上下に移動します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="51a3b-268">矢印が横に表示する必要がありますを手がジェスチャのフレームの端に近づくと、追跡手札を警告する、カーソルが失われます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="51a3b-269">矢印は、損失を防止の追跡を防ぐために手を移動する方向を示します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="51a3b-270">第 4 章 - 操作</span><span class="sxs-lookup"><span data-stu-id="51a3b-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="51a3b-271">目標</span><span class="sxs-lookup"><span data-stu-id="51a3b-271">Objectives</span></span>

* <span data-ttu-id="51a3b-272">操作イベントを使用すると、自分の手で「宇宙飛行士を移動できます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="51a3b-273">ユーザーが操作を使用するタイミングを把握できるカーソル上でフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="51a3b-274">手順</span><span class="sxs-lookup"><span data-stu-id="51a3b-274">Instructions</span></span>

<span data-ttu-id="51a3b-275">GestureManager.cs と AstronautManager.cs により、次の操作。</span><span class="sxs-lookup"><span data-stu-id="51a3b-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="51a3b-276">音声キーワードを使用して"**移動「宇宙飛行士**"有効にする**操作**ジェスチャと"**回転飛行士**"を無効にします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="51a3b-277">応答に切り替えて、**操作のジェスチャ レコグナイザー**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="51a3b-278">それでは始めましょう。</span><span class="sxs-lookup"><span data-stu-id="51a3b-278">Let's get started.</span></span>

1. <span data-ttu-id="51a3b-279">**階層**パネルで、新しい空の GameObject を作成します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="51a3b-280">名前を付けます"**AstronautManager**"。</span><span class="sxs-lookup"><span data-stu-id="51a3b-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="51a3b-281">**インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="51a3b-282">メニューで、検索ボックスに入力**飛行士 Manager**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="51a3b-283">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-283">Select the search result.</span></span>
4. <span data-ttu-id="51a3b-284">**インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="51a3b-285">メニューで、検索ボックスに入力**音声入力ソース**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="51a3b-286">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-286">Select the search result.</span></span>

<span data-ttu-id="51a3b-287">これで、「宇宙飛行士の相互作用の状態を制御するために必要な音声コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="51a3b-288">展開、**キーワード**セクション、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="51a3b-289">をクリックして、 **+** 右側に新しいキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="51a3b-290">As キーワードを入力 **「宇宙飛行士を移動**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="51a3b-291">自由に必要な場合は、キーのショートカットを追加します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="51a3b-292">をクリックして、 **+** 右側に新しいキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="51a3b-293">As キーワードを入力 **「宇宙飛行士を回転**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="51a3b-294">自由に必要な場合は、キーのショートカットを追加します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="51a3b-295">対応するハンドラーのコードが見つかります**GestureAction.cs**の**ISpeechHandler.OnSpeechKeywordRecognized**ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="51a3b-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![第 4 章の音声入力ソースをセットアップする方法](images/holograms211-speech.png)

<span data-ttu-id="51a3b-297">次に、カーソル上で操作のフィードバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="51a3b-298">**プロジェクト**パネル**ホログラム**フォルダー、検索、 **PathingFeedback**資産。</span><span class="sxs-lookup"><span data-stu-id="51a3b-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="51a3b-299">ドラッグ アンド ドロップ、 **PathingFeedback**にプレハブ、 **CursorWithFeedback**オブジェクト、**階層**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="51a3b-300">**階層**パネルで、をクリックして**CursorWithFeedback**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="51a3b-301">ドラッグ アンド ドロップ、 **PathingFeedback**オブジェクトから、**階層**上に、**のゲーム オブジェクトの検出パス**プロパティ、**カーソル フィードバック**コンポーネント、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="51a3b-302">コードを追加する必要があります**GestureAction.cs**以下を有効にします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="51a3b-303">コードを追加、 **IManipulationHandler.OnManipulationUpdated** 、関数は、「宇宙飛行士を移動するときに、**操作**ジェスチャが検出されました。</span><span class="sxs-lookup"><span data-stu-id="51a3b-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="51a3b-304">計算、**動きベクトル**飛行士の移動先を決定するベースの手元に位置します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="51a3b-305">**移動**を新しい位置に「宇宙飛行士します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="51a3b-306">4.a を練習する完全なコーディング**GestureAction.cs**、または完成したソリューションは、以下を使用します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="51a3b-307">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="51a3b-307">Build and Deploy</span></span>

* <span data-ttu-id="51a3b-308">Unity で再構築し、ビルドして、HoloLens でアプリを実行する Visual Studio からデプロイします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="51a3b-309">HoloLens の前に手を移動し、追跡できるように、人差し指を発生させます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="51a3b-310">「宇宙飛行士経由でカーソルをを注目します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="51a3b-311">操作のジェスチャに「宇宙飛行士を移動する ' 飛行士の移動 と答えてください。</span><span class="sxs-lookup"><span data-stu-id="51a3b-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="51a3b-312">4 つの矢印は、プログラムが操作イベントに応答するようになりましたことを示すカーソルの周囲に表示されます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="51a3b-313">親指まで、人差し指を削減し、一緒に挟まれてしておきます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="51a3b-314">「宇宙飛行士はも移動手周囲を移動すると、(これは操作です)。</span><span class="sxs-lookup"><span data-stu-id="51a3b-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="51a3b-315">「宇宙飛行士操作を停止する際人差し指を発生させます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="51a3b-316">注:手を移動する前に、' 飛行士移動 ' はいないと答えるとは、ナビゲーションのジェスチャを代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="51a3b-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="51a3b-317">'回転「宇宙飛行士' 回転可能な状態に戻すことあるとします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="51a3b-318">第 5 章「モデルの拡張</span><span class="sxs-lookup"><span data-stu-id="51a3b-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="51a3b-319">目標</span><span class="sxs-lookup"><span data-stu-id="51a3b-319">Objectives</span></span>

* <span data-ttu-id="51a3b-320">複数「宇宙飛行士モデルを展開しユーザーが対話できることをより小さな部分。</span><span class="sxs-lookup"><span data-stu-id="51a3b-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="51a3b-321">移動および操作のジェスチャを使用して個別に各部分に移動します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="51a3b-322">手順</span><span class="sxs-lookup"><span data-stu-id="51a3b-322">Instructions</span></span>

<span data-ttu-id="51a3b-323">このセクションでは、次のタスクを行いましています。</span><span class="sxs-lookup"><span data-stu-id="51a3b-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="51a3b-324">New キーワードを追加"**展開モデル**"を「宇宙飛行士モデルを展開します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="51a3b-325">New キーワードを追加"**リセット モデル**"に、モデルを元のフォームに戻ります。</span><span class="sxs-lookup"><span data-stu-id="51a3b-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="51a3b-326">前の章から音声入力ソースに 2 つ以上のキーワードを追加することでこれを実行します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="51a3b-327">認識のイベントを処理する別の方法も示します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="51a3b-328">[戻る] をクリックして**AstronautManager**で、**インスペクター**を展開し、**キーワード**セクション、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="51a3b-329">をクリックして、 **+** 右側に新しいキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="51a3b-330">As キーワードを入力**展開モデル**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="51a3b-331">自由に必要な場合は、キーのショートカットを追加します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="51a3b-332">をクリックして、 **+** 右側に新しいキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="51a3b-333">As キーワードを入力**モデルをリセット**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="51a3b-334">自由に必要な場合は、キーのショートカットを追加します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="51a3b-335">**インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="51a3b-336">メニューで、検索ボックスに入力**音声入力ハンドラー**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="51a3b-337">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-337">Select the search result.</span></span>
8. <span data-ttu-id="51a3b-338">確認**はグローバル リスナー**を絞っているこれらのコマンドを GameObject に関係なく機能するため、します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="51a3b-339">をクリックして、 **+** ボタンをクリックし、選択**展開モデル**キーワードのドロップダウン リストから。</span><span class="sxs-lookup"><span data-stu-id="51a3b-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="51a3b-340">をクリックして、 **+** 応答、およびドラッグ下、 **AstronautManager**から、**階層**に、 **None (オブジェクト)** フィールド。</span><span class="sxs-lookup"><span data-stu-id="51a3b-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="51a3b-341">をクリックして、**いいえ関数**] ドロップダウンで、[ **AstronautManager**、し**ExpandModelCommand**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="51a3b-342">音声入力ハンドラーをクリックします。 **+** ボタンをクリックし、選択**リセット モデル**キーワードのドロップダウン リストから。</span><span class="sxs-lookup"><span data-stu-id="51a3b-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="51a3b-343">をクリックして、 **+** 応答、およびドラッグ下、 **AstronautManager**から、**階層**に、 **None (オブジェクト)** フィールド。</span><span class="sxs-lookup"><span data-stu-id="51a3b-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="51a3b-344">をクリックして、**いいえ関数**] ドロップダウンで、[ **AstronautManager**、し**ResetModelCommand**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![第 5 章のセットアップ、音声入力ソースとハンドラーする方法](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="51a3b-346">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="51a3b-346">Build and Deploy</span></span>

* <span data-ttu-id="51a3b-347">お試しください。</span><span class="sxs-lookup"><span data-stu-id="51a3b-347">Try it!</span></span> <span data-ttu-id="51a3b-348">ビルドして、アプリ、HoloLens をデプロイします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="51a3b-349">たとえば**展開モデル**に展開されている「宇宙飛行士モデルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="51a3b-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="51a3b-350">使用**ナビゲーション**飛行士スーツの各部分を回転させる。</span><span class="sxs-lookup"><span data-stu-id="51a3b-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="51a3b-351">たとえば**移動「宇宙飛行士**しを使用して**操作**飛行士スーツの各部分を移動しますします。</span><span class="sxs-lookup"><span data-stu-id="51a3b-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="51a3b-352">たとえば**回転飛行士**部分を再度回転。</span><span class="sxs-lookup"><span data-stu-id="51a3b-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="51a3b-353">たとえば**リセット モデル**に、「宇宙飛行士元フォームに戻ります。</span><span class="sxs-lookup"><span data-stu-id="51a3b-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="51a3b-354">最後です</span><span class="sxs-lookup"><span data-stu-id="51a3b-354">The End</span></span>

<span data-ttu-id="51a3b-355">これで終了です。</span><span class="sxs-lookup"><span data-stu-id="51a3b-355">Congratulations!</span></span> <span data-ttu-id="51a3b-356">完了したので**MR 入力 211。ジェスチャ**します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="51a3b-357">検出し、追跡、ナビゲーション、および操作イベントを渡すために応答する方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="51a3b-358">移動および操作のジェスチャの違いを理解します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="51a3b-359">手の形が検出されると、手が失われると、オブジェクトが別の相互作用 (ナビゲーション vs 操作) をサポートする場合は、視覚的なフィードバックを提供する、カーソルを変更する方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="51a3b-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
