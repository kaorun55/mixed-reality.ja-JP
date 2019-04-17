---
title: 作業開始
description: このガイドでは、複合現実の開発を起動して実行を取得する最も簡単な方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: get started, basics, HoloLens, immersive headset, ar, vr, unity, visual studio, quick start, how to
ms.openlocfilehash: 92fbc6eee227da571ff36401f84cf81a093062d7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601344"
---
# <a name="get-started"></a><span data-ttu-id="e6ee0-104">作業開始</span><span class="sxs-lookup"><span data-stu-id="e6ee0-104">Get started</span></span>

<span data-ttu-id="e6ee0-105">複合現実の開発の世界へようこそ。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-105">Welcome to the world of mixed reality development!</span></span> <span data-ttu-id="e6ee0-106">MR を新しい場合は、このガイドは、ハブ取得して、実行可能な限り早くになります。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-106">If you're new to MR, this guide will be your hub to get up and running as quickly as possible.</span></span> <span data-ttu-id="e6ee0-107">開発用 PC のセットを取得し、デバイスを準備して、MR 開発プロセスの速度がツールをインストールするをお手伝いします。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-107">We'll help you get your PC set up for development, get your device(s) ready, and install tools that will speed up the MR development process.</span></span> 

## <a name="intro-to-mixed-reality"></a><span data-ttu-id="e6ee0-108">複合現実の概要</span><span class="sxs-lookup"><span data-stu-id="e6ee0-108">Intro to mixed reality</span></span>

<span data-ttu-id="e6ee0-109">"Mixed reality"意味し、拡張現実 (AR) に関連付ける方法については、いくつか質問がある可能性があり、仮想現実 (VR)。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-109">You may have some questions about what we mean by "mixed reality" and how it relates to augmented reality (AR) and virtual reality (VR).</span></span> <span data-ttu-id="e6ee0-110">つまり、複合現実、拡張現実から情報を網羅したスペクトルのために、デジタルの世界と現実の世界のブレンド現実の世界で、仮想現実に、現実の世界がほぼすべてが、デジタル コンテンツの配置デジタルで置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-110">In short, mixed reality is the blending of the physical world with the digital world, so it's a spectrum that covers everything from augmented reality, where digital content is placed in the real world, to virtual reality, where your real world is almost entirely replaced by the digital.</span></span> 

<span data-ttu-id="e6ee0-111">![HoloLens と没入型の (VR) ヘッドセットの両方をサポートする複合現実アプリの例](images/mr-island.png)</span><span class="sxs-lookup"><span data-stu-id="e6ee0-111">![Example of a mixed reality app that supports both HoloLens and immersive (VR) headsets](images/mr-island.png)</span></span><br>
<span data-ttu-id="e6ee0-112">*複合現実アプリは、HoloLens と没入型の (VR) ヘッドセットの両方をサポートできます。*</span><span class="sxs-lookup"><span data-stu-id="e6ee0-112">*Mixed reality apps can support both HoloLens and immersive (VR) headsets*</span></span>

<span data-ttu-id="e6ee0-113">1 つの開発プラットフォームと、MR スペクトルに対応できるツールのセットとして Windows Mixed Reality を作成したと現在同じ範囲をカバーする 2 つのデバイスの種類をサポートしています。[Microsoft HoloLens](https://www.microsoft.com/hololens)、世界最初自己完結型 holographic ヘッドセット、および[Windows Mixed Reality イマーシブ ヘッドセットとアニメーション コント ローラー](https://www.microsoft.com/windows/windows-mixed-reality)、強力な仮想現実エクスペリエンスのために、PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-113">We created Windows Mixed Reality as a single development platform and set of tools that can cover the MR spectrum, and we currently support two device types that cover the same spectrum: [Microsoft HoloLens](https://www.microsoft.com/hololens), the world's first self-contained holographic headset, and [Windows Mixed Reality immersive headsets and motion controllers](https://www.microsoft.com/windows/windows-mixed-reality), which connect to a PC for powerful virtual reality experiences.</span></span> <span data-ttu-id="e6ee0-114">チェック アウト、何が [mixed reality ですか?](関心がある場合の詳しい回答に関する記事です。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-114">You can check out our What is [mixed reality?]( article for a more thorough answer if you're interested.</span></span>

## <a name="choose-your-development-path"></a><span data-ttu-id="e6ee0-115">開発パスを選択します。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-115">Choose your development path</span></span>

<span data-ttu-id="e6ee0-116">Mixed reality アプリを開発する最も簡単な方法を使用して[Unity](https://unity3d.com)、ゲーム開発の多くの場合に使用されるミドルウェアが強力で人気のあるツールです。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-116">The easiest way to develop a mixed reality app is using [Unity](https://unity3d.com), a powerful and popular middleware tool often used for game development.</span></span> <span data-ttu-id="e6ee0-117">カスタム エンジンを使用する場合は、することもできます[DirectX に対してビルド](directx-development-overview.md)が MR のほとんどの開発者が、ゲームやアプリに Unity を使用します。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-117">If you want to use a custom engine, you can also [build against DirectX](directx-development-overview.md), but most MR developers use Unity for their games and apps.</span></span> <span data-ttu-id="e6ee0-118">Unity を使用した、HoloLens、没入型の (VR) ヘッドセットまたはその両方を対象とする複合現実アプリを作成するようになります。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-118">With Unity you'll be able to create a mixed reality app that targets HoloLens, immersive (VR) headsets, or both!</span></span>

## <a name="prepare-your-pc-and-devices-for-development"></a><span data-ttu-id="e6ee0-119">PC とデバイス開発を準備します。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-119">Prepare your PC and devices for development</span></span>

<span data-ttu-id="e6ee0-120">HoloLens、没入型の (VR) ヘッドセットまたはその両方を対象とする mixed reality アプリをビルドしているかどうかは、一般的な一連のツールと Api を使用しているします。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-120">Whether you're building a mixed reality app that targets HoloLens, immersive (VR) headsets, or both, you'll be using a common set of tools and APIs.</span></span> <span data-ttu-id="e6ee0-121">また、お使いの PC が足りずに行う開発のためかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-121">You'll also want to make sure your PC is powerful enough for the development you'll be doing.</span></span> 

>[!NOTE]
><span data-ttu-id="e6ee0-122">開発用 PC の推奨事項の仕様、各ソフトウェア ツールのサポートされているバージョンと関連する設定や構成は、それぞれのノートを確認できます、[ツールをインストールする](install-the-tools.md)記事。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-122">You can find our recommendations on development PC specs, supported versions of each software tool, and relevant settings or configuration notes for each in the [Install the tools](install-the-tools.md) article.</span></span> <span data-ttu-id="e6ee0-123">以下のツールをインストールする前に、その記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-123">Please review that article before installing the tools below.</span></span>

<span data-ttu-id="e6ee0-124">インストールするツール:</span><span class="sxs-lookup"><span data-stu-id="e6ee0-124">Tools to install:</span></span>
* [<span data-ttu-id="e6ee0-125">Unity</span><span class="sxs-lookup"><span data-stu-id="e6ee0-125">Unity</span></span>](https://store.unity.com/download)
* [<span data-ttu-id="e6ee0-126">Visual Studio (windows 10 SDK)</span><span class="sxs-lookup"><span data-stu-id="e6ee0-126">Visual Studio (with Windows 10 SDK)</span></span>](https://developer.microsoft.com/windows/downloads)
* [<span data-ttu-id="e6ee0-127">Unity for mixed Reality ツールキット</span><span class="sxs-lookup"><span data-stu-id="e6ee0-127">Mixed Reality Toolkit for Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

<span data-ttu-id="e6ee0-128">たいも[開発者モードに、ターゲット デバイスを配置し、ターゲット デバイスにアプリを展開するための Visual Studio の構成](using-visual-studio.md)します。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-128">You'll also want to [put your target device into Developer mode and configure Visual Studio for deploying apps to the target device](using-visual-studio.md).</span></span>

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="e6ee0-129">Unity の混在の現実 Toolkit に関する注意事項</span><span class="sxs-lookup"><span data-stu-id="e6ee0-129">A note about the Mixed Reality Toolkit for Unity</span></span>

![Unity の MRTK](images/mrtkandunity.png)<br>

<span data-ttu-id="e6ee0-131">***これを具体化してなぜ MRTK UNITY は、驚くほどすばらしいものがあり内:) 教えください YOYO***</span><span class="sxs-lookup"><span data-stu-id="e6ee0-131">***YOYO PLEASE FLESH THIS OUT AND TELL EVERYONE WHY MRTK-UNITY IS SO AMAZING AND ALL THE COOL THINGS IT HAS INSIDE :)***</span></span>

<span data-ttu-id="e6ee0-132">Mixed Reality Toolkit は、スクリプトのコレクションと、コンポーネントは、Microsoft HoloLens と Windows Mixed Reality ヘッドセットを対象とするアプリケーションの開発を加速対象としています。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-132">The Mixed Reality Toolkit is a collection of scripts and components intended to accelerate development of applications targeting Microsoft HoloLens and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="e6ee0-133">プロジェクトの目的は、複合現実のアプリケーションを作成しすべての拡大に伴い、コミュニティに貢献するエントリに対する障壁を削減です。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-133">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span>

## <a name="start-your-first-mr-project"></a><span data-ttu-id="e6ee0-134">最初、MR プロジェクトを開始します。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-134">Start your first MR project</span></span>

<span data-ttu-id="e6ee0-135">これで、PC とデバイスのセットアップ時に、Unity での最初の複合現実プロジェクトを作成する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-135">Now that your PC and device(s) are set up, you're ready to create your first mixed reality project in Unity.</span></span> <span data-ttu-id="e6ee0-136">最初、MR academy コースの手順に従う[MR 基本 100。Unity の概要](holograms-100.md)、終了するまでは、キューブ、mixed reality ヘッドセットで起動し実行を必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-136">Follow along with our first MR academy course, [MR Basics 100: Getting started with Unity](holograms-100.md), and by the end you'll have a cube up and running in a mixed reality headset.</span></span>

<span data-ttu-id="e6ee0-137">![複合現実の Unity プロジェクトで、キューブのスクリーン ショット](images/mr-cube.PNG)</span><span class="sxs-lookup"><span data-stu-id="e6ee0-137">![Screenshot of a cube in a mixed reality Unity project](images/mr-cube.PNG)</span></span><br>
<span data-ttu-id="e6ee0-138">*Unity - hello world で最初の複合現実プロジェクト。*</span><span class="sxs-lookup"><span data-stu-id="e6ee0-138">*Your first mixed reality project in Unity - hello world!*</span></span>

## <a name="learn-more-and-get-help"></a><span data-ttu-id="e6ee0-139">詳細については、ヘルプを表示</span><span class="sxs-lookup"><span data-stu-id="e6ee0-139">Learn more and get help</span></span>

<span data-ttu-id="e6ee0-140">最初の MR プロジェクトを正常に作成したが、詳細については、おそらく空腹できました!</span><span class="sxs-lookup"><span data-stu-id="e6ee0-140">Now that you've successfully created your first MR project, you're probably hungry for more!</span></span> <span data-ttu-id="e6ee0-141">必要がありますに役立つリソースを次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-141">Here are some resources that should help:</span></span>
* <span data-ttu-id="e6ee0-142">[実際には開発者向けドキュメントを混在](mixed-reality.md)- いるここがある技術ドキュメント、設計のガイダンス、サンプル プロジェクト、およびケース スタディなどをチェック アウト、さらに多くします。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-142">[Mixed reality developer documentation](mixed-reality.md) - you're already here, but there's so much more to check out, including technical documentation, design guidance, sample projects, and case studies.</span></span>
* <span data-ttu-id="e6ee0-143">[複合現実 academy](academy.md) -MR のコア ビルディング ブロックを実装するためのプロジェクトの設定を網羅するチュートリアルの手順に従って、MR アプリにクラウド サービスに Azure を統合します。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-143">[Mixed reality academy](academy.md) - follow along with tutorials covering everything from setting up projects, to implementing core MR building blocks, to integrating Azure cloud services into your MR app.</span></span>
* <span data-ttu-id="e6ee0-144">[Unity の学習](https://unity3d.com/learn)-Unity の web サイトは、チュートリアル、プロジェクト、およびライブ トレーニング セッション creators learning の各段階でします。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-144">[Learn Unity](https://unity3d.com/learn) - Unity's website offers tutorials, projects, and live training sessions for creators at every stage of learning.</span></span>

<span data-ttu-id="e6ee0-145">これらの優れたコミュニティ リソースからヘルプを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-145">You can also get help from these great community resources:</span></span>
* <span data-ttu-id="e6ee0-146">[開発者向けフォーラムに、複合現実](https://forums.hololens.com/)-質問し質問に答えるだけでなく MR 開発関連のニュースを直接 Microsoft から読み取りを複合現実の開発者向けの公式のフォーラムです。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-146">[Mixed reality developer forums](https://forums.hololens.com/) - the official forum for mixed reality developers to ask and answer questions, as well as read MR development news straight from Microsoft.</span></span>
* <span data-ttu-id="e6ee0-147">[HoloDevelopers Slack チャネル](https://holodevelopersslack.azurewebsites.net/)-最も堅牢な機知を持ち合わせて外部が実際には固有の開発者のチャネルを混在。 ここで、開発者は、知識が豊富で便利です。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-147">[HoloDevelopers Slack channel](https://holodevelopersslack.azurewebsites.net/) - the most robust and resourceful external mixed reality-specific developer channel; the devs here are knowledgeable and helpful.</span></span>
* <span data-ttu-id="e6ee0-148">[Unity フォーラム](https://forum.unity3d.com/)-Unity の公式フォーラム。</span><span class="sxs-lookup"><span data-stu-id="e6ee0-148">[Unity forums](https://forum.unity3d.com/) - Unity's official forums.</span></span>
