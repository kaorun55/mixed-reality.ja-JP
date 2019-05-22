---
title: MR 入力 212 - 音声
description: 音声の概念の詳細については、Unity、Visual Studio および HoloLens を使用してこのコーディング チュートリアルに従ってください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit unity、academy、チュートリアルでは、音声
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598924"
---
>[!NOTE]
><span data-ttu-id="4043d-104">Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4043d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="4043d-105">そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。</span><span class="sxs-lookup"><span data-stu-id="4043d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="4043d-106">これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。</span><span class="sxs-lookup"><span data-stu-id="4043d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="4043d-107">サポートされているデバイスで作業を続行するが保持されます。</span><span class="sxs-lookup"><span data-stu-id="4043d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="4043d-108">一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。</span><span class="sxs-lookup"><span data-stu-id="4043d-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="4043d-109">この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。</span><span class="sxs-lookup"><span data-stu-id="4043d-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="4043d-110">MR 入力 212:音声</span><span class="sxs-lookup"><span data-stu-id="4043d-110">MR Input 212: Voice</span></span>

<span data-ttu-id="4043d-111">[音声入力](voice-input.md)により、当社ホログラムと対話することもできます。</span><span class="sxs-lookup"><span data-stu-id="4043d-111">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="4043d-112">音声コマンドは、非常に自然で簡単な方法で機能します。</span><span class="sxs-lookup"><span data-stu-id="4043d-112">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="4043d-113">されるので、音声コマンドを設計します。</span><span class="sxs-lookup"><span data-stu-id="4043d-113">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="4043d-114">自然です</span><span class="sxs-lookup"><span data-stu-id="4043d-114">Natural</span></span>
* <span data-ttu-id="4043d-115">覚えやすい</span><span class="sxs-lookup"><span data-stu-id="4043d-115">Easy to remember</span></span>
* <span data-ttu-id="4043d-116">適切なコンテキスト</span><span class="sxs-lookup"><span data-stu-id="4043d-116">Context appropriate</span></span>
* <span data-ttu-id="4043d-117">同じコンテキスト内でその他のオプションを十分に区別</span><span class="sxs-lookup"><span data-stu-id="4043d-117">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="4043d-118">[MR 基本 101](holograms-101.md)、2 つの単純な音声コマンドの作成に、KeywordRecognizer を使いました。</span><span class="sxs-lookup"><span data-stu-id="4043d-118">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="4043d-119">MR 入力 212 でをについて詳しく知るし、学習する方法。</span><span class="sxs-lookup"><span data-stu-id="4043d-119">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="4043d-120">HoloLens の音声認識エンジン用に最適化された音声コマンドをデザインします。</span><span class="sxs-lookup"><span data-stu-id="4043d-120">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="4043d-121">コマンドの使用可能なは、どのような音声に注意してください、ユーザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="4043d-121">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="4043d-122">ユーザーの音声コマンドいただいてを確認します。</span><span class="sxs-lookup"><span data-stu-id="4043d-122">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="4043d-123">ユーザーを理解という、ディクテーション認識エンジンを使用します。</span><span class="sxs-lookup"><span data-stu-id="4043d-123">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="4043d-124">SRGS、または音声認識文法仕様ファイルに基づいてコマンドをリッスンするには、文法の認識エンジンを使用します。</span><span class="sxs-lookup"><span data-stu-id="4043d-124">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="4043d-125">このコースで思いますモデル エクスプ ローラーに組み込まれています[MR 入力 210](holograms-210.md)と[MR 入力 211](holograms-211.md)します。</span><span class="sxs-lookup"><span data-stu-id="4043d-125">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="4043d-126">以前のバージョンの Unity と Mixed Reality Toolkit を使用して、以下の各章に埋め込まれたビデオが記録されています。</span><span class="sxs-lookup"><span data-stu-id="4043d-126">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="4043d-127">詳細な手順については、正確かつ最新ですが、スクリプトとは、無効な対応するビデオの中でビジュアルを表示があります。</span><span class="sxs-lookup"><span data-stu-id="4043d-127">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="4043d-128">ビデオでは、後生のために含まれる保持され、概念説明のため、引き続き適用されます。</span><span class="sxs-lookup"><span data-stu-id="4043d-128">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="4043d-129">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="4043d-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4043d-130">コース</span><span class="sxs-lookup"><span data-stu-id="4043d-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="4043d-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="4043d-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="4043d-132"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="4043d-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="4043d-133">MR 入力 212:音声</span><span class="sxs-lookup"><span data-stu-id="4043d-133">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="4043d-134">✔️</span><span class="sxs-lookup"><span data-stu-id="4043d-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="4043d-135">✔️</span><span class="sxs-lookup"><span data-stu-id="4043d-135">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="4043d-136">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="4043d-136">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="4043d-137">前提条件</span><span class="sxs-lookup"><span data-stu-id="4043d-137">Prerequisites</span></span>

* <span data-ttu-id="4043d-138">正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="4043d-138">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="4043d-139">基本的なC#プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="4043d-139">Some basic C# programming ability.</span></span>
* <span data-ttu-id="4043d-140">完了する必要があります[MR 基本 101](holograms-101.md)します。</span><span class="sxs-lookup"><span data-stu-id="4043d-140">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="4043d-141">完了する必要があります[MR 入力 210](holograms-210.md)します。</span><span class="sxs-lookup"><span data-stu-id="4043d-141">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="4043d-142">完了する必要があります[MR 入力 211](holograms-211.md)します。</span><span class="sxs-lookup"><span data-stu-id="4043d-142">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="4043d-143">HoloLens デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。</span><span class="sxs-lookup"><span data-stu-id="4043d-143">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="4043d-144">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="4043d-144">Project files</span></span>

* <span data-ttu-id="4043d-145">ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip)プロジェクトに必要です。</span><span class="sxs-lookup"><span data-stu-id="4043d-145">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="4043d-146">Unity 2017.2 またはそれ以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="4043d-146">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="4043d-147">解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。</span><span class="sxs-lookup"><span data-stu-id="4043d-147">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="4043d-148">をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)します。</span><span class="sxs-lookup"><span data-stu-id="4043d-148">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="4043d-149">正誤表と注意事項</span><span class="sxs-lookup"><span data-stu-id="4043d-149">Errata and Notes</span></span>

* <span data-ttu-id="4043d-150">「マイ コードのみを有効にする」無効にする必要があります (*unchecked*) -> ツールの Visual Studio でのオプションには、デバッグ、コードにブレークポイントをヒットするには-> です。</span><span class="sxs-lookup"><span data-stu-id="4043d-150">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="4043d-151">Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="4043d-151">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="4043d-152">手順</span><span class="sxs-lookup"><span data-stu-id="4043d-152">Instructions</span></span>

1. <span data-ttu-id="4043d-153">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="4043d-153">Start Unity.</span></span>
2. <span data-ttu-id="4043d-154">**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4043d-154">Select **Open**.</span></span>
3. <span data-ttu-id="4043d-155">移動し、 **HolographicAcademy ホログラム 212 音声**フォルダー以前されていないアーカイブします。</span><span class="sxs-lookup"><span data-stu-id="4043d-155">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="4043d-156">検索し、選択、**開始**/**モデル エクスプ ローラー**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="4043d-156">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="4043d-157">をクリックして、**フォルダーの選択**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4043d-157">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="4043d-158">**プロジェクト**パネルで、展開、**シーン**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="4043d-158">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="4043d-159">ダブルクリック**ModelExplorer**シーン Unity で読み込めません。</span><span class="sxs-lookup"><span data-stu-id="4043d-159">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="4043d-160">ビルド</span><span class="sxs-lookup"><span data-stu-id="4043d-160">Building</span></span>

1. <span data-ttu-id="4043d-161">Unity では、次のように選択します。**ファイル > Build Settings**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-161">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="4043d-162">場合**シーン/ModelExplorer**に記載されていない**Scenes In Build**、 をクリックして**開くシーンを追加**シーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="4043d-162">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="4043d-163">具体的には、HoloLens の開発中、設定**ターゲット デバイス**に**HoloLens**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-163">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="4043d-164">それ以外の場合、残して**任意のデバイス**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-164">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="4043d-165">確認**ビルド タイプ**に設定されている**D3D**と**SDK**に設定されている**インストールされている最新**(16299 またはそれ以降の SDK がある必要があります)。</span><span class="sxs-lookup"><span data-stu-id="4043d-165">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="4043d-166">**[Build]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4043d-166">Click **Build**.</span></span>
6. <span data-ttu-id="4043d-167">作成、**新しいフォルダー** "App"という名前です。</span><span class="sxs-lookup"><span data-stu-id="4043d-167">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="4043d-168">1 回のクリック、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="4043d-168">Single click the **App** folder.</span></span>
8. <span data-ttu-id="4043d-169">キーを押して**フォルダーの選択**Unity は Visual Studio のプロジェクトのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="4043d-169">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="4043d-170">Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4043d-170">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="4043d-171">開く、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="4043d-171">Open the **App** folder.</span></span>
2. <span data-ttu-id="4043d-172">開く、 **ModelExplorer Visual Studio ソリューション**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-172">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="4043d-173">HoloLens へのデプロイ: 場合</span><span class="sxs-lookup"><span data-stu-id="4043d-173">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="4043d-174">デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x86**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-174">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="4043d-175">ローカル コンピューター] ボタンの横の矢印のドロップダウンをクリックし、[**リモート マシン**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-175">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="4043d-176">入力**HoloLens デバイスの IP アドレス**認証モードを設定および**ユニバーサル (暗号化されていないプロトコル)** します。</span><span class="sxs-lookup"><span data-stu-id="4043d-176">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="4043d-177">クリックして**選択**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-177">Click **Select**.</span></span> <span data-ttu-id="4043d-178">デバイスの IP アドレスがわからない場合に参照**設定 > ネットワークとインターネット > 詳細オプション**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="4043d-179">上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="4043d-180">最初に、デバイスに展開するには、する必要があります[Visual Studio をペアリング](using-visual-studio.md#pairing-your-device-hololens)します。</span><span class="sxs-lookup"><span data-stu-id="4043d-180">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="4043d-181">アプリが展開されると、消去、 **Fitbox**で、**ジェスチャ を選択**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-181">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="4043d-182">場合は、イマーシブ ヘッドセットへのデプロイ。</span><span class="sxs-lookup"><span data-stu-id="4043d-182">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="4043d-183">デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x64**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="4043d-184">必ず、配置ターゲットに設定されて**ローカル マシン**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-184">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="4043d-185">上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-185">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="4043d-186">アプリが展開されると、消去、 **Fitbox**アニメーション コント ローラーで、トリガーを取得することによって。</span><span class="sxs-lookup"><span data-stu-id="4043d-186">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="4043d-187">Visual Studio でエラー パネルの赤いエラーの一部が分かります。</span><span class="sxs-lookup"><span data-stu-id="4043d-187">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="4043d-188">それらを無視しても安全になります。</span><span class="sxs-lookup"><span data-stu-id="4043d-188">It is safe to ignore them.</span></span> <span data-ttu-id="4043d-189">ビルドの進行状況を実際に表示する出力パネルへの切り替え。</span><span class="sxs-lookup"><span data-stu-id="4043d-189">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="4043d-190">エラー出力 パネルにでは修正プログラム (ほとんどの多くの場合、スクリプトで間違いに起因) を作成することが必要です。</span><span class="sxs-lookup"><span data-stu-id="4043d-190">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="4043d-191">第 1 章 - 認識</span><span class="sxs-lookup"><span data-stu-id="4043d-191">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="4043d-192">目標</span><span class="sxs-lookup"><span data-stu-id="4043d-192">Objectives</span></span>

* <span data-ttu-id="4043d-193">について説明します、**注意事項**の音声コマンド デザインします。</span><span class="sxs-lookup"><span data-stu-id="4043d-193">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="4043d-194">使用**KeywordRecognizer**視線入力ベースの音声コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="4043d-194">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="4043d-195">ユーザーがカーソルを使用して音声コマンドを認識させる**フィードバック**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-195">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="4043d-196">音声コマンド デザイン</span><span class="sxs-lookup"><span data-stu-id="4043d-196">Voice Command Design</span></span>

<span data-ttu-id="4043d-197">この章では音声コマンドを設計する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4043d-197">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="4043d-198">音声コマンドを作成する: 場合</span><span class="sxs-lookup"><span data-stu-id="4043d-198">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="4043d-199">DO</span><span class="sxs-lookup"><span data-stu-id="4043d-199">DO</span></span>

* <span data-ttu-id="4043d-200">簡潔なコマンドを作成します。</span><span class="sxs-lookup"><span data-stu-id="4043d-200">Create concise commands.</span></span> <span data-ttu-id="4043d-201">使用しない *「現在選択されているビデオを再生」*、そのコマンドが簡潔でないし、ユーザーが簡単に未定義の状態があるためです。</span><span class="sxs-lookup"><span data-stu-id="4043d-201">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="4043d-202">代わりに、次のように使用する必要があります。*「ビデオを再生」*、簡潔であり複数音節文字があります。</span><span class="sxs-lookup"><span data-stu-id="4043d-202">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="4043d-203">単純なボキャブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="4043d-203">Use a simple vocabulary.</span></span> <span data-ttu-id="4043d-204">常に共通の単語や語句を検出し、保存、ユーザーが容易であるを使用してください。</span><span class="sxs-lookup"><span data-stu-id="4043d-204">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="4043d-205">たとえば、アプリケーションに表示または非表示になりますが、注オブジェクトがある場合はいないコマンドを使用する *「プラカードを表示」*「プラカード」はめったに使用される用語であるためです。</span><span class="sxs-lookup"><span data-stu-id="4043d-205">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="4043d-206">代わりに、コマンドを使用します。*「メモを表示する」* アプリケーションの注意事項を表示します。</span><span class="sxs-lookup"><span data-stu-id="4043d-206">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="4043d-207">一貫性を保ちます。</span><span class="sxs-lookup"><span data-stu-id="4043d-207">Be consistent.</span></span> <span data-ttu-id="4043d-208">音声コマンド、アプリケーション全体が一貫性のある保持される必要があります。</span><span class="sxs-lookup"><span data-stu-id="4043d-208">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="4043d-209">2 つのシーン、アプリケーションであり、その両方のシーンは、アプリケーションを終了するためのボタンを含めることが想像してみてください。</span><span class="sxs-lookup"><span data-stu-id="4043d-209">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="4043d-210">最初のシーンは、コマンドを使用する場合 *"Exit"* シーンがコマンドを使用する、ボタンが 2 番目のトリガーを *「アプリを閉じる」* ユーザーが混乱するからです。</span><span class="sxs-lookup"><span data-stu-id="4043d-210">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="4043d-211">複数のシーン間で同じ機能が解決しない場合、それをトリガーする同じ音声コマンドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4043d-211">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="4043d-212">できません</span><span class="sxs-lookup"><span data-stu-id="4043d-212">DON'T</span></span>

* <span data-ttu-id="4043d-213">1 つ音節コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4043d-213">Use single syllable commands.</span></span> <span data-ttu-id="4043d-214">例として、音声、ビデオを再生するコマンドを作成する場合を避ける必要があります、単純なコマンドを使用して *「再生」* 音節は 1 つのみであり、システムで簡単に見落とされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4043d-214">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="4043d-215">代わりに、次のように使用する必要があります。*「ビデオを再生」*、簡潔であり複数音節文字があります。</span><span class="sxs-lookup"><span data-stu-id="4043d-215">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="4043d-216">システムのコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4043d-216">Use system commands.</span></span> <span data-ttu-id="4043d-217">*"Select"* コマンドは、現在フォーカスがあるオブジェクトのタップ イベントをトリガーする、システムによって予約されています。</span><span class="sxs-lookup"><span data-stu-id="4043d-217">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="4043d-218">再使用しない、 *"Select"* キーワードまたは語句のコマンドは期待どおりには動作しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4043d-218">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="4043d-219">などの場合は、アプリケーションでキューブを選択するための音声コマンドが *「キューブの選択」* ユーザーが求めていた球体で、コマンドを載せた、ときに球は、代わりに、選択した後、します。</span><span class="sxs-lookup"><span data-stu-id="4043d-219">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="4043d-220">同様にアプリ バーのコマンドは、ボイスが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="4043d-220">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="4043d-221">CoreWindow ビューでは、次のような音声コマンドを使用しません。</span><span class="sxs-lookup"><span data-stu-id="4043d-221">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="4043d-222">戻ってください</span><span class="sxs-lookup"><span data-stu-id="4043d-222">Go Back</span></span>
    2. <span data-ttu-id="4043d-223">スクロール ツール</span><span class="sxs-lookup"><span data-stu-id="4043d-223">Scroll Tool</span></span>
    3. <span data-ttu-id="4043d-224">ズーム ツール</span><span class="sxs-lookup"><span data-stu-id="4043d-224">Zoom Tool</span></span>
    4. <span data-ttu-id="4043d-225">ドラッグ ツール</span><span class="sxs-lookup"><span data-stu-id="4043d-225">Drag Tool</span></span>
    5. <span data-ttu-id="4043d-226">Adjust</span><span class="sxs-lookup"><span data-stu-id="4043d-226">Adjust</span></span>
    6. <span data-ttu-id="4043d-227">Remove</span><span class="sxs-lookup"><span data-stu-id="4043d-227">Remove</span></span>
* <span data-ttu-id="4043d-228">ようなサウンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4043d-228">Use similar sounds.</span></span> <span data-ttu-id="4043d-229">広げると覚える音声コマンドを使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="4043d-229">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="4043d-230">サポート ショッピング アプリケーションがあれば *「ストアの表示」* と *「詳細」* し、もう一方を使用していたときに、コマンドのいずれかを無効にすると、同様の音声コマンド。</span><span class="sxs-lookup"><span data-stu-id="4043d-230">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="4043d-231">たとえば、使用する可能性があります、 *「を表示する格納」* 、ストアを開くボタンをクリックし、ストアが表示されたときにそのコマンドを無効にできるように、 *「詳細」* コマンドが参照される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4043d-231">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="4043d-232">手順</span><span class="sxs-lookup"><span data-stu-id="4043d-232">Instructions</span></span>

* <span data-ttu-id="4043d-233">Unity の**階層**パネルで、検索する検索ツールを使用して、 **holoComm_screen_mesh**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4043d-233">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="4043d-234">ダブルクリックして、 **holoComm_screen_mesh**でそれを表示するオブジェクト、**シーン**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-234">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="4043d-235">これは、「宇宙飛行士のウォッチ式は、音声コマンドに応答します。</span><span class="sxs-lookup"><span data-stu-id="4043d-235">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="4043d-236">**インスペクター**パネルで、検索、**音声入力ソース (スクリプト)** コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="4043d-236">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="4043d-237">展開、**キーワード**セクションには、サポートされている音声コマンド。**Communicator を開く**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-237">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="4043d-238">右側にある歯車アイコンをクリックし、選択**スクリプトの編集**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-238">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="4043d-239">探索**SpeechInputSource.cs**で使用する方法を理解する、 **KeywordRecognizer**音声コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="4043d-239">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="4043d-240">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="4043d-240">Build and Deploy</span></span>

* <span data-ttu-id="4043d-241">Unity では、次のように使用します。**ファイル > Build Settings** 、アプリケーションをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="4043d-241">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="4043d-242">開く、**アプリ**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="4043d-242">Open the **App** folder.</span></span>
* <span data-ttu-id="4043d-243">開く、 **ModelExplorer Visual Studio ソリューション**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-243">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="4043d-244">(既にビルド/展開して Visual Studio では、このプロジェクトのセットアップ中に場合、し、VS のインスタンスを開いて 'すべて再読み込み' が表示されたらクリックします)。</span><span class="sxs-lookup"><span data-stu-id="4043d-244">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="4043d-245">Visual Studio で、次のようにクリックします。**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-245">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="4043d-246">アプリケーションのデプロイは、HoloLens 後に、合わせる ボックスを使用して、閉じ、[エア タップ](gestures.md#air-tap)ジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="4043d-246">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gestures.md#air-tap) gesture.</span></span>
* <span data-ttu-id="4043d-247">「宇宙飛行士ウォッチを見つめます。</span><span class="sxs-lookup"><span data-stu-id="4043d-247">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="4043d-248">ウォッチにフォーカスがある場合は、カーソルがマイクに変更されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4043d-248">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="4043d-249">これは、音声コマンドをアプリケーションがリッスンしてフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="4043d-249">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="4043d-250">Watch でツールヒントが表示されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4043d-250">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="4043d-251">これにより、ユーザーの検出、 *"開いている Communicator"* コマンド。</span><span class="sxs-lookup"><span data-stu-id="4043d-251">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="4043d-252">ウォッチで gazing、中に答えて *"開く Communicator"* communicator パネルを開きます。</span><span class="sxs-lookup"><span data-stu-id="4043d-252">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="4043d-253">第 2 章 – 受信確認</span><span class="sxs-lookup"><span data-stu-id="4043d-253">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="4043d-254">目標</span><span class="sxs-lookup"><span data-stu-id="4043d-254">Objectives</span></span>

* <span data-ttu-id="4043d-255">マイクの入力を使用してメッセージを記録します。</span><span class="sxs-lookup"><span data-stu-id="4043d-255">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="4043d-256">アプリケーションがそれぞれの声をリッスンしていることをユーザーにフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="4043d-256">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="4043d-257">**マイク**マイクから記録するアプリの機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4043d-257">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="4043d-258">これを行うことを既に MR 入力 212、ただしこれ独自のプロジェクトに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4043d-258">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="4043d-259">Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」に移動して、player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="4043d-259">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="4043d-260">"ユニバーサル Windows プラットフォーム タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4043d-260">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="4043d-261">「発行の設定 > 機能」セクションでは、確認、**マイク**機能</span><span class="sxs-lookup"><span data-stu-id="4043d-261">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="4043d-262">手順</span><span class="sxs-lookup"><span data-stu-id="4043d-262">Instructions</span></span>

* <span data-ttu-id="4043d-263">Unity の**階層**パネルで、ことを確認します、 **holoComm_screen_mesh**オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="4043d-263">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="4043d-264">**インスペクター**パネルで、検索、**飛行士ウォッチ (スクリプト)** コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="4043d-264">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="4043d-265">値として設定されますが、小さな青いキューブをクリックして、 **Communicator Prefab**プロパティ。</span><span class="sxs-lookup"><span data-stu-id="4043d-265">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="4043d-266">**プロジェクト**パネル、 **Communicator**プレハブはフォーカスがあるようになりました。</span><span class="sxs-lookup"><span data-stu-id="4043d-266">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="4043d-267">をクリックして、 **Communicator**のプレハブ、**プロジェクト**でそのコンポーネントを表示するパネル、**インスペクター**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-267">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="4043d-268">見て、**マイク マネージャー (スクリプト)** コンポーネント、これにより、ユーザーの音声を記録します。</span><span class="sxs-lookup"><span data-stu-id="4043d-268">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="4043d-269">注意、 **Communicator**オブジェクトには、**音声入力ハンドラー (スクリプト)** コンポーネントへの応答を**メッセージの送信**コマンド。</span><span class="sxs-lookup"><span data-stu-id="4043d-269">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="4043d-270">見て、 **Communicator (スクリプト)** コンポーネントと Visual Studio で開くスクリプトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="4043d-270">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="4043d-271">Communicator.cs は communicator のデバイスで適切なボタンの状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="4043d-271">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="4043d-272">これによって、ユーザー メッセージを記録、再生、および、飛行士にメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="4043d-272">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="4043d-273">開始もとそれぞれの声が聞こえたことをユーザーに確認をアニメーション化された波フォームを停止します。</span><span class="sxs-lookup"><span data-stu-id="4043d-273">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="4043d-274">**Communicator.cs**から次の行 (81 および 82) を削除、**開始**メソッド。</span><span class="sxs-lookup"><span data-stu-id="4043d-274">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="4043d-275">これは、communicator の 'Record' ボタンを有効になります。</span><span class="sxs-lookup"><span data-stu-id="4043d-275">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="4043d-276">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="4043d-276">Build and Deploy</span></span>

* <span data-ttu-id="4043d-277">Visual Studio で、アプリケーションをリビルドし、デバイスに展開します。</span><span class="sxs-lookup"><span data-stu-id="4043d-277">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="4043d-278">「宇宙飛行士ウォッチ見つめますと答えて *"開いている Communicator"* 、communicator を表示します。</span><span class="sxs-lookup"><span data-stu-id="4043d-278">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="4043d-279">キーを押して、**レコード**口頭でメッセージを「宇宙飛行士記録を開始するボタン (マイク)。</span><span class="sxs-lookup"><span data-stu-id="4043d-279">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="4043d-280">、読み上げを開始し、wave アニメーションの再生、communicator では、ユーザーにフィードバックを提供するには、それぞれの声を聞いたことのことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4043d-280">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="4043d-281">キーを押して、**停止**(四角形の左) ボタンをクリックし、wave アニメーションが実行を停止していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4043d-281">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="4043d-282">キーを押して、**再生** (直角三角形)、記録されたメッセージを再生し、デバイスをお待ちしております。</span><span class="sxs-lookup"><span data-stu-id="4043d-282">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="4043d-283">キーを押して、**停止**ボタン (右の正方形)、記録されたメッセージの再生を停止します。</span><span class="sxs-lookup"><span data-stu-id="4043d-283">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="4043d-284">たとえば *「メッセージの送信」* communicator を閉じてから、「宇宙飛行士 'メッセージが受信した' 応答を受信しますします。</span><span class="sxs-lookup"><span data-stu-id="4043d-284">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="4043d-285">第 3 章 - ディクテーション認識エンジンと理解</span><span class="sxs-lookup"><span data-stu-id="4043d-285">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="4043d-286">目標</span><span class="sxs-lookup"><span data-stu-id="4043d-286">Objectives</span></span>

* <span data-ttu-id="4043d-287">ディクテーション認識エンジンを使用して、ユーザーの音声をテキストに変換します。</span><span class="sxs-lookup"><span data-stu-id="4043d-287">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="4043d-288">Communicator でディクテーション認識エンジンの仮説と最終的な結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="4043d-288">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="4043d-289">この章でディクテーション認識エンジン、飛行士に対するメッセージの作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="4043d-289">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="4043d-290">ディクテーション認識エンジンを使用する場合に注意します。</span><span class="sxs-lookup"><span data-stu-id="4043d-290">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="4043d-291">作業をディクテーション認識エンジンの WiFi に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4043d-291">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="4043d-292">タイムアウトは、一定期間の後に発生します。</span><span class="sxs-lookup"><span data-stu-id="4043d-292">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="4043d-293">注意すべき 2 つのタイムアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="4043d-293">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="4043d-294">認識エンジンが起動し、最初の 5 秒間のオーディオの声が場合、タイムアウトになります。</span><span class="sxs-lookup"><span data-stu-id="4043d-294">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="4043d-295">認識エンジンが指定の結果を 20 秒の無音が場合がタイムアウトになります。</span><span class="sxs-lookup"><span data-stu-id="4043d-295">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="4043d-296">(キーワードまたはディクテーション) 認識エンジンの 1 つだけの型は、いつでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="4043d-296">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="4043d-297">**マイク**マイクから記録するアプリの機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4043d-297">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="4043d-298">これを行うことを既に MR 入力 212、ただしこれ独自のプロジェクトに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4043d-298">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="4043d-299">Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」に移動して、player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="4043d-299">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="4043d-300">"ユニバーサル Windows プラットフォーム タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4043d-300">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="4043d-301">「発行の設定 > 機能」セクションでは、確認、**マイク**機能</span><span class="sxs-lookup"><span data-stu-id="4043d-301">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="4043d-302">手順</span><span class="sxs-lookup"><span data-stu-id="4043d-302">Instructions</span></span>

<span data-ttu-id="4043d-303">編集しようとして**MicrophoneManager.cs**ディクテーション認識エンジンを使用します。</span><span class="sxs-lookup"><span data-stu-id="4043d-303">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="4043d-304">これは、追加します。</span><span class="sxs-lookup"><span data-stu-id="4043d-304">This is what we'll add:</span></span>

1. <span data-ttu-id="4043d-305">ときに、**録画ボタン**は、押された、 **、DictationRecognizer を開始**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-305">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="4043d-306">表示、**仮説**DictationRecognizer が認識されるのです。</span><span class="sxs-lookup"><span data-stu-id="4043d-306">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="4043d-307">内のロック、**結果**DictationRecognizer が認識されるのです。</span><span class="sxs-lookup"><span data-stu-id="4043d-307">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="4043d-308">DictationRecognizer タイムアウトを確認します。</span><span class="sxs-lookup"><span data-stu-id="4043d-308">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="4043d-309">ときに、**停止ボタン**が押された mic セッションがタイムアウトまたは **、DictationRecognizer を停止**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-309">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="4043d-310">再起動、 **KeywordRecognizer**、リッスン、**メッセージの送信**コマンド。</span><span class="sxs-lookup"><span data-stu-id="4043d-310">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="4043d-311">それでは始めましょう。</span><span class="sxs-lookup"><span data-stu-id="4043d-311">Let's get started.</span></span> <span data-ttu-id="4043d-312">3. a でのコーディングの練習をすべて完了**MicrophoneManager.cs**、またはコピーして、下の完成したコードを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="4043d-312">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone. 
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="4043d-313">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="4043d-313">Build and Deploy</span></span>

* <span data-ttu-id="4043d-314">Visual Studio での再構築し、デバイスに展開します。</span><span class="sxs-lookup"><span data-stu-id="4043d-314">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="4043d-315">エア タップ ジェスチャに合わせるボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4043d-315">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="4043d-316">「宇宙飛行士ウォッチ見つめますと答えて *"開いている Communicator"* します。</span><span class="sxs-lookup"><span data-stu-id="4043d-316">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="4043d-317">選択、**レコード**ボタン (マイク)、メッセージを記録します。</span><span class="sxs-lookup"><span data-stu-id="4043d-317">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="4043d-318">読み上げを開始します。</span><span class="sxs-lookup"><span data-stu-id="4043d-318">Start speaking.</span></span> <span data-ttu-id="4043d-319">**ディクテーション認識エンジン**音声を解釈し、communicator の仮説のテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="4043d-319">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="4043d-320">格言をお試しください *「メッセージの送信」* メッセージを記録している間です。</span><span class="sxs-lookup"><span data-stu-id="4043d-320">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="4043d-321">注意、**キーワード認識エンジン**ために、応答しません、**ディクテーション認識エンジン**アクティブなままです。</span><span class="sxs-lookup"><span data-stu-id="4043d-321">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="4043d-322">数秒の読み上げを停止します。</span><span class="sxs-lookup"><span data-stu-id="4043d-322">Stop speaking for a few seconds.</span></span> <span data-ttu-id="4043d-323">観察ディクテーション認識エンジンがその仮説を完了して、最終的な結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="4043d-323">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="4043d-324">読み上げを開始し、20 秒間一時停止します。</span><span class="sxs-lookup"><span data-stu-id="4043d-324">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="4043d-325">これにより、**ディクテーション認識エンジン**タイムアウトにします。</span><span class="sxs-lookup"><span data-stu-id="4043d-325">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="4043d-326">注意、**キーワード認識エンジン**が上記のタイムアウト後に再度有効にします。</span><span class="sxs-lookup"><span data-stu-id="4043d-326">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="4043d-327">Communicator は、音声コマンドに応答ようになりました。</span><span class="sxs-lookup"><span data-stu-id="4043d-327">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="4043d-328">たとえば *「メッセージの送信」* 飛行士にメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="4043d-328">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="4043d-329">第 4 章 - 音声認識の文法</span><span class="sxs-lookup"><span data-stu-id="4043d-329">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="4043d-330">目標</span><span class="sxs-lookup"><span data-stu-id="4043d-330">Objectives</span></span>

* <span data-ttu-id="4043d-331">に従って SRGS、または音声認識文法仕様ファイルをユーザーの音声認識文法認識エンジンを使用します。</span><span class="sxs-lookup"><span data-stu-id="4043d-331">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="4043d-332">**マイク**マイクから記録するアプリの機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4043d-332">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="4043d-333">これを行うことを既に MR 入力 212、ただしこれ独自のプロジェクトに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4043d-333">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="4043d-334">Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」に移動して、player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="4043d-334">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="4043d-335">"ユニバーサル Windows プラットフォーム タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4043d-335">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="4043d-336">「発行の設定 > 機能」セクションでは、確認、**マイク**機能</span><span class="sxs-lookup"><span data-stu-id="4043d-336">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="4043d-337">手順</span><span class="sxs-lookup"><span data-stu-id="4043d-337">Instructions</span></span>

1. <span data-ttu-id="4043d-338">**階層**パネルで、検索**Jetpack_Center**して選択します。</span><span class="sxs-lookup"><span data-stu-id="4043d-338">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="4043d-339">探して、**末尾アクション**でスクリプトを作成、**インスペクター**パネル。</span><span class="sxs-lookup"><span data-stu-id="4043d-339">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="4043d-340">右側の小さな円をクリックして、**オブジェクトをタグに沿った**フィールド。</span><span class="sxs-lookup"><span data-stu-id="4043d-340">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="4043d-341">ウィンドウが表示されたら、検索**SRGSToolbox**し、一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="4043d-341">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="4043d-342">見て、 **SRGSColor.xml**ファイル、 **StreamingAssets**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="4043d-342">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
* <span data-ttu-id="4043d-343">SRGS の設計仕様は、W3C web サイトで確認できます[ここ](https://www.w3.org/TR/speech-grammar/)します。</span><span class="sxs-lookup"><span data-stu-id="4043d-343">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>
* <span data-ttu-id="4043d-344">SRGS ファイルでは、次の 3 つの種類のルールがあります。</span><span class="sxs-lookup"><span data-stu-id="4043d-344">In our SRGS file, we have three types of rules:</span></span>
  * <span data-ttu-id="4043d-345">12 個の色の一覧から 1 つの色とするルール。</span><span class="sxs-lookup"><span data-stu-id="4043d-345">A rule which lets you say one color from a list of twelve colors.</span></span>
  * <span data-ttu-id="4043d-346">色のルールと 3 つの図形の 1 つの組み合わせをリッスンする 3 つの規則。</span><span class="sxs-lookup"><span data-stu-id="4043d-346">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
  * <span data-ttu-id="4043d-347">ルート ルールでは、colorChooser で、次の 3 つの「色 + 図形の」ルールの任意の組み合わせをリッスンします。</span><span class="sxs-lookup"><span data-stu-id="4043d-347">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="4043d-348">任意の順序で、どんな量の 3 つすべてを 1 つだけで、図形と言えます。</span><span class="sxs-lookup"><span data-stu-id="4043d-348">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="4043d-349">これは、最初にファイルの上部にあるルート規則として指定されているのルールのみが、リッスンが&lt;文法&gt;タグ。</span><span class="sxs-lookup"><span data-stu-id="4043d-349">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="4043d-350">構築し、デプロイ</span><span class="sxs-lookup"><span data-stu-id="4043d-350">Build and Deploy</span></span>

* <span data-ttu-id="4043d-351">Unity では、アプリケーションをリビルドし、ビルド HoloLens でアプリを体験する Visual Studio からデプロイします。</span><span class="sxs-lookup"><span data-stu-id="4043d-351">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="4043d-352">エア タップ ジェスチャに合わせるボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4043d-352">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="4043d-353">「宇宙飛行士の jetpack 見つめますとをエア タップ ジェスチャを実行します。</span><span class="sxs-lookup"><span data-stu-id="4043d-353">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="4043d-354">読み上げを開始します。</span><span class="sxs-lookup"><span data-stu-id="4043d-354">Start speaking.</span></span> <span data-ttu-id="4043d-355">**文法レコグナイザー**音声を解釈し、認識に基づいて図形の色を変更します。</span><span class="sxs-lookup"><span data-stu-id="4043d-355">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="4043d-356">コマンドの例は、「青色、黄色の正方形」です。</span><span class="sxs-lookup"><span data-stu-id="4043d-356">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="4043d-357">ツールボックスを消去する別のエア タップ ジェスチャを実行します。</span><span class="sxs-lookup"><span data-stu-id="4043d-357">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="4043d-358">最後です</span><span class="sxs-lookup"><span data-stu-id="4043d-358">The End</span></span>

<span data-ttu-id="4043d-359">これで終了です。</span><span class="sxs-lookup"><span data-stu-id="4043d-359">Congratulations!</span></span> <span data-ttu-id="4043d-360">完了したので**MR 入力 212。音声**します。</span><span class="sxs-lookup"><span data-stu-id="4043d-360">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="4043d-361">Dos および音声コマンドのすべきでないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4043d-361">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="4043d-362">ユーザーに音声コマンドを認識するツールヒントが採用された方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="4043d-362">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="4043d-363">複数の種類のフィードバックを使用して、ユーザーの声が聞こえたのことを確認しました。</span><span class="sxs-lookup"><span data-stu-id="4043d-363">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="4043d-364">キーワード認識とディクテーション認識エンジンを切り替える方法について説明し、これら 2 つの機能が理解し、音声を解釈する方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="4043d-364">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="4043d-365">アプリケーションで音声認識、SRGS ファイルと文法認識エンジンを使用する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="4043d-365">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>
