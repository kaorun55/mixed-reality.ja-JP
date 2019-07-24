---
title: 作業開始
description: このガイドでは、mixed reality 開発を最大限に活用するための最も簡単な方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: はじめに、基本、HoloLens、イマーシブヘッドセット、ar、vr、unity、visual studio、クイックスタート、方法
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873958"
---
# <a name="get-started"></a><span data-ttu-id="ee3c9-104">作業開始</span><span class="sxs-lookup"><span data-stu-id="ee3c9-104">Get started</span></span>

<span data-ttu-id="ee3c9-105">Mixed reality 開発の世界へようこそ!</span><span class="sxs-lookup"><span data-stu-id="ee3c9-105">Welcome to the world of mixed reality development!</span></span> <span data-ttu-id="ee3c9-106">MR を初めてご利用の場合、このガイドはできるだけ早く稼働させることができます。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-106">If you're new to MR, this guide will be your hub to get up and running as quickly as possible.</span></span> <span data-ttu-id="ee3c9-107">開発用に PC をセットアップし、デバイスを準備し、MR 開発プロセスを高速化するツールをインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-107">We'll help you get your PC set up for development, get your device(s) ready, and install tools that will speed up the MR development process.</span></span> 

## <a name="intro-to-mixed-reality"></a><span data-ttu-id="ee3c9-108">Mixed reality の概要</span><span class="sxs-lookup"><span data-stu-id="ee3c9-108">Intro to mixed reality</span></span>

<span data-ttu-id="ee3c9-109">"Mixed reality" によって何を意味するか、およびそれが拡張現実 (AR) と仮想現実 (VR) とどのように関連しているかについて、いくつかの質問があるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-109">You may have some questions about what we mean by "mixed reality" and how it relates to augmented reality (AR) and virtual reality (VR).</span></span> <span data-ttu-id="ee3c9-110">簡潔に言えば、混合現実とは、世界的な世界とデジタルの世界を合わせたものです。これは、実際の世界では、デジタルコンテンツが現実の世界に配置され、実質的にはほぼ完全にデジタルで置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-110">In short, mixed reality is the blending of the physical world with the digital world, so it's a spectrum that covers everything from augmented reality, where digital content is placed in the real world, to virtual reality, where your real world is almost entirely replaced by the digital.</span></span> 

<span data-ttu-id="ee3c9-111">![HoloLens とイマーシブ (VR) ヘッドセットの両方をサポートする mixed reality アプリの例](images/mr-island.png)</span><span class="sxs-lookup"><span data-stu-id="ee3c9-111">![Example of a mixed reality app that supports both HoloLens and immersive (VR) headsets](images/mr-island.png)</span></span><br>
<span data-ttu-id="ee3c9-112">*Mixed reality アプリでは、HoloLens とイマーシブ (VR) ヘッドセットの両方をサポートできます。*</span><span class="sxs-lookup"><span data-stu-id="ee3c9-112">*Mixed reality apps can support both HoloLens and immersive (VR) headsets*</span></span>

<span data-ttu-id="ee3c9-113">Windows Mixed Reality を1つの開発プラットフォームとして、MR スペクトルに対応できるツールのセットとして作成しました。現在、同じ範囲をカバーする2種類のデバイスをサポートしています。[Microsoft HoloLens](https://www.microsoft.com/hololens)は、世界初の自己完結型の holographic ヘッドセットであり、 [Windows Mixed reality のイマーシブヘッドセットとモーションコントローラー](https://www.microsoft.com/windows/windows-mixed-reality)で、強力な仮想現実エクスペリエンスを実現するために PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-113">We created Windows Mixed Reality as a single development platform and set of tools that can cover the MR spectrum, and we currently support two device types that cover the same spectrum: [Microsoft HoloLens](https://www.microsoft.com/hololens), the world's first self-contained holographic headset, and [Windows Mixed Reality immersive headsets and motion controllers](https://www.microsoft.com/windows/windows-mixed-reality), which connect to a PC for powerful virtual reality experiences.</span></span> <span data-ttu-id="ee3c9-114">[Mixed reality] を確認できます。(詳細については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-114">You can check out our What is [mixed reality?]( article for a more thorough answer if you're interested.</span></span>

## <a name="choose-your-development-path"></a><span data-ttu-id="ee3c9-115">開発パスの選択</span><span class="sxs-lookup"><span data-stu-id="ee3c9-115">Choose your development path</span></span>

<span data-ttu-id="ee3c9-116">Mixed reality アプリを開発する最も簡単な方法は、ゲーム開発によく使用される強力で人気のあるミドルウェアツールである[Unity](https://unity3d.com)を使用することです。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-116">The easiest way to develop a mixed reality app is using [Unity](https://unity3d.com), a powerful and popular middleware tool often used for game development.</span></span> <span data-ttu-id="ee3c9-117">カスタムエンジンを使用する場合は、 [DirectX に対してビルド](directx-development-overview.md)することもできますが、ほとんどの MR 開発者は、ゲームやアプリに Unity を使用します。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-117">If you want to use a custom engine, you can also [build against DirectX](directx-development-overview.md), but most MR developers use Unity for their games and apps.</span></span> <span data-ttu-id="ee3c9-118">Unity を使用すると、HoloLens、イマーシブ (VR) ヘッドホン、またはその両方を対象とする mixed reality アプリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-118">With Unity you'll be able to create a mixed reality app that targets HoloLens, immersive (VR) headsets, or both!</span></span>

## <a name="prepare-your-pc-and-devices-for-development"></a><span data-ttu-id="ee3c9-119">開発用に PC とデバイスを準備する</span><span class="sxs-lookup"><span data-stu-id="ee3c9-119">Prepare your PC and devices for development</span></span>

<span data-ttu-id="ee3c9-120">HoloLens、イマーシブ (VR) ヘッドホン、またはその両方を対象とする mixed reality アプリを構築している場合でも、一般的なツールと Api のセットを使用します。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-120">Whether you're building a mixed reality app that targets HoloLens, immersive (VR) headsets, or both, you'll be using a common set of tools and APIs.</span></span> <span data-ttu-id="ee3c9-121">また、お客様の PC が、開発を行うために十分な性能を備えていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-121">You'll also want to make sure your PC is powerful enough for the development you'll be doing.</span></span> 

>[!NOTE]
><span data-ttu-id="ee3c9-122">開発用 PC の仕様、各ソフトウェアツールのサポートされているバージョン、および関連する設定や構成に関する注意事項については、「[ツールのインストール](install-the-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-122">You can find our recommendations on development PC specs, supported versions of each software tool, and relevant settings or configuration notes for each in the [Install the tools](install-the-tools.md) article.</span></span> <span data-ttu-id="ee3c9-123">以下のツールをインストールする前に、この記事を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-123">Please review that article before installing the tools below.</span></span>

<span data-ttu-id="ee3c9-124">インストールするツール:</span><span class="sxs-lookup"><span data-stu-id="ee3c9-124">Tools to install:</span></span>
* [<span data-ttu-id="ee3c9-125">Unity</span><span class="sxs-lookup"><span data-stu-id="ee3c9-125">Unity</span></span>](https://store.unity.com/download)
* [<span data-ttu-id="ee3c9-126">Visual Studio (Windows 10 SDK を使用)</span><span class="sxs-lookup"><span data-stu-id="ee3c9-126">Visual Studio (with Windows 10 SDK)</span></span>](https://developer.microsoft.com/windows/downloads)
* [<span data-ttu-id="ee3c9-127">Unity 用 Mixed Reality ツールキット</span><span class="sxs-lookup"><span data-stu-id="ee3c9-127">Mixed Reality Toolkit for Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

<span data-ttu-id="ee3c9-128">また、[ターゲットデバイスを開発者モードにし、アプリをターゲットデバイスにデプロイするように Visual Studio を構成](using-visual-studio.md)することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-128">You'll also want to [put your target device into Developer mode and configure Visual Studio for deploying apps to the target device](using-visual-studio.md).</span></span>

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="ee3c9-129">Mixed Reality Toolkit for Unity に関する注意事項</span><span class="sxs-lookup"><span data-stu-id="ee3c9-129">A note about the Mixed Reality Toolkit for Unity</span></span>

![Unity の MRTK](images/mrtkandunity.png)<br>

<span data-ttu-id="ee3c9-131">***具体化さんは、MRTK-UNITY が非常に優れていて、それがどのようなものであるのかを誰かに伝えて:) います。***</span><span class="sxs-lookup"><span data-stu-id="ee3c9-131">***YOYO PLEASE FLESH THIS OUT AND TELL EVERYONE WHY MRTK-UNITY IS SO AMAZING AND ALL THE COOL THINGS IT HAS INSIDE :)***</span></span>

<span data-ttu-id="ee3c9-132">Mixed Reality Toolkit は、Microsoft HoloLens および Windows Mixed Reality ヘッドセットを対象とするアプリケーションの開発を促進するためのスクリプトとコンポーネントのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-132">The Mixed Reality Toolkit is a collection of scripts and components intended to accelerate development of applications targeting Microsoft HoloLens and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="ee3c9-133">このプロジェクトは、Mixed Reality アプリケーション作成への参入の障壁を減らし、私たち全員の成長とともにコミュニティに貢献することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-133">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span>

## <a name="start-your-first-mr-project"></a><span data-ttu-id="ee3c9-134">最初の MR プロジェクトを開始する</span><span class="sxs-lookup"><span data-stu-id="ee3c9-134">Start your first MR project</span></span>

<span data-ttu-id="ee3c9-135">PC とデバイスが設定されたので、Unity で最初の mixed reality プロジェクトを作成する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-135">Now that your PC and device(s) are set up, you're ready to create your first mixed reality project in Unity.</span></span> <span data-ttu-id="ee3c9-136">Mr の最初の mr academy コース、 [mr 基本100に従ってください。Unity](holograms-100.md)を使ってみると、複合現実のヘッドセットでキューブを作成し、実行することになります。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-136">Follow along with our first MR academy course, [MR Basics 100: Getting started with Unity](holograms-100.md), and by the end you'll have a cube up and running in a mixed reality headset.</span></span>

<span data-ttu-id="ee3c9-137">![Mixed reality Unity プロジェクトのキューブのスクリーンショット](images/mr-cube.PNG)</span><span class="sxs-lookup"><span data-stu-id="ee3c9-137">![Screenshot of a cube in a mixed reality Unity project](images/mr-cube.PNG)</span></span><br>
<span data-ttu-id="ee3c9-138">*Unity の最初の mixed reality プロジェクト。*</span><span class="sxs-lookup"><span data-stu-id="ee3c9-138">*Your first mixed reality project in Unity - hello world!*</span></span>

## <a name="learn-more-and-get-help"></a><span data-ttu-id="ee3c9-139">詳細情報とヘルプの表示</span><span class="sxs-lookup"><span data-stu-id="ee3c9-139">Learn more and get help</span></span>

<span data-ttu-id="ee3c9-140">最初の MR プロジェクトが正常に作成されたので、もっと多くのことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-140">Now that you've successfully created your first MR project, you're probably hungry for more!</span></span> <span data-ttu-id="ee3c9-141">次のリソースを参考にしてください。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-141">Here are some resources that should help:</span></span>
* <span data-ttu-id="ee3c9-142">[Mixed reality 開発者向けドキュメント](mixed-reality.md)-既にお持ちですが、技術ドキュメント、設計ガイダンス、サンプルプロジェクト、ケーススタディなど、さらに多くのことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-142">[Mixed reality developer documentation](mixed-reality.md) - you're already here, but there's so much more to check out, including technical documentation, design guidance, sample projects, and case studies.</span></span>
* <span data-ttu-id="ee3c9-143">[Mixed reality チュートリアル](tutorials.md)-プロジェクトの設定、core mr 構成ブロックの実装、mr アプリへの Azure cloud services の統合に関するすべての情報を網羅したチュートリアルに従ってください。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-143">[Mixed reality tutorials](tutorials.md) - follow along with tutorials covering everything from setting up projects, to implementing core MR building blocks, to integrating Azure cloud services into your MR app.</span></span>
* <span data-ttu-id="ee3c9-144">[Unity について説明](https://unity3d.com/learn)します。 unity の web サイトでは、学習のすべての段階で作成者のためのチュートリアル、プロジェクト、ライブトレーニングセッションを提供しています。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-144">[Learn Unity](https://unity3d.com/learn) - Unity's website offers tutorials, projects, and live training sessions for creators at every stage of learning.</span></span>

<span data-ttu-id="ee3c9-145">また、次のような優れたコミュニティリソースから支援を受けることもできます。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-145">You can also get help from these great community resources:</span></span>
* <span data-ttu-id="ee3c9-146">[Mixed reality 開発](https://forums.hololens.com/)者向けフォーラム-mixed reality 開発者向けの公式フォーラムです。 Microsoft から直接寄せられた MR 開発ニュースである質問に回答したり、回答したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-146">[Mixed reality developer forums](https://forums.hololens.com/) - the official forum for mixed reality developers to ask and answer questions, as well as read MR development news straight from Microsoft.</span></span>
* <span data-ttu-id="ee3c9-147">[HoloDevelopers の余裕期間チャネル](https://holodevelopersslack.azurewebsites.net/)-最も堅牢かつ機知の外部混合の現実固有の開発者チャネル。ここでは、開発者を参考にしてください。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-147">[HoloDevelopers Slack channel](https://holodevelopersslack.azurewebsites.net/) - the most robust and resourceful external mixed reality-specific developer channel; the devs here are knowledgeable and helpful.</span></span>
* <span data-ttu-id="ee3c9-148">[Unity フォーラム](https://forum.unity3d.com/)-unity の公式フォーラム。</span><span class="sxs-lookup"><span data-stu-id="ee3c9-148">[Unity forums](https://forum.unity3d.com/) - Unity's official forums.</span></span>
