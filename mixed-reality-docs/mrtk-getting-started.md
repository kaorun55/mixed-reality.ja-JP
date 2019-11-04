---
title: MRTK バージョン2の概要
description: MRTK の活用に関心がある新しい開発者向け
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality、test、Mixed Reality Toolkit、MRTK バージョン2、MRTK、tools、SDK、HoloLens、HoloLens 2
ms.openlocfilehash: 46a06b951ae9aa60259f70be3fa1e558e7ab8ab6
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438346"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="9a950-104">MRTK v2 の概要</span><span class="sxs-lookup"><span data-stu-id="9a950-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="9a950-105">MRTK はじめにガイド</span><span class="sxs-lookup"><span data-stu-id="9a950-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="9a950-106">MRTK V2 の概要については、「 [mrtk ファーストステップガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a950-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for detailed information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="9a950-107">Mixed Reality Toolkit (MRTK) とは</span><span class="sxs-lookup"><span data-stu-id="9a950-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="9a950-108">MRTK は、HoloLens が最初にリリースされた後に行われていたすばらしいオープンソースのツールキットであり、現在のところ、開発者コミュニティが提供されているので、このツールキットを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="9a950-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="9a950-109">過去3年間、microsoft は開発者コミュニティのフィードバックを受け、最大の関心事を考慮するために MRTK v2 を構築しました。</span><span class="sxs-lookup"><span data-stu-id="9a950-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="9a950-110">Unity での MRTK v2 は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="9a950-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="9a950-111">MRTK バージョン 2 は、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="9a950-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="9a950-112">このプロジェクトは、Mixed Reality アプリケーション作成への参入の障壁を減らし、私たち全員の成長とともにコミュニティに貢献することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="9a950-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 

<span data-ttu-id="9a950-113">詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a950-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="9a950-114">MRTK v2 の新バージョン</span><span class="sxs-lookup"><span data-stu-id="9a950-114">New with MRTK v2</span></span>
<span data-ttu-id="9a950-115">これらのプラットフォームツールに対するコミットメントを重視したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="9a950-115">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="9a950-116">実際、MRTK バージョン2を利用して、setup experience (OOBE) や Mixed Reality Learning アプリケーションなどの受信トレイエクスペリエンスを開発しました。</span><span class="sxs-lookup"><span data-stu-id="9a950-116">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="9a950-117">また、プラットフォームで開発するのに最適な方法であると考えられるため、新しい HoloLens 2 機能が MRTK を通じて最初に公開されることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="9a950-117">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="9a950-118">方式</span><span class="sxs-lookup"><span data-stu-id="9a950-118">Modular</span></span>
<span data-ttu-id="9a950-119">モジュール型の方法でビルドしたため、ツールキットをすべてプロジェクトに取り込む必要がありません。</span><span class="sxs-lookup"><span data-stu-id="9a950-119">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="9a950-120">これには、実際にいくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="9a950-120">There are actually a few benefits to this.</span></span>  <span data-ttu-id="9a950-121">これにより、プロジェクトのサイズが小さくなり、管理も容易になります。</span><span class="sxs-lookup"><span data-stu-id="9a950-121">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="9a950-122">それに加えて、スクリプト可能なオブジェクトを使用して構築され、インターフェイスによって駆動されるため、独自のに含まれているコンポーネントを置き換えることで、他のサービス、システム、およびプラットフォームをサポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9a950-122">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="9a950-123">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="9a950-123">Cross-platform</span></span>
<span data-ttu-id="9a950-124">他のプラットフォームの場合は、クロスプラットフォームのサポートがあります。</span><span class="sxs-lookup"><span data-stu-id="9a950-124">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="9a950-125">これは、すべての単一プラットフォームが既定でサポートされているわけではありませんが、ビルドターゲットを他のプラットフォームに切り替えると、どのツールキットコードも破損しないようにしました。</span><span class="sxs-lookup"><span data-stu-id="9a950-125">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="9a950-126">モジュール型の設計による堅牢性と拡張性により、ARCore、Arcore、OpenVR などの複数のプラットフォームをサポートするための優れたパスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="9a950-126">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="9a950-127">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="9a950-127">Performant</span></span>
<span data-ttu-id="9a950-128">モバイルプラットフォームを使用すると、パフォーマンスを考慮して構築されています。</span><span class="sxs-lookup"><span data-stu-id="9a950-128">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="9a950-129">これは非常に重要であり、ツールがお客様に対して機能しないようにする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="9a950-129">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a950-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a950-130">See also</span></span>
* [<span data-ttu-id="9a950-131">MRTK ファーストステップガイド</span><span class="sxs-lookup"><span data-stu-id="9a950-131">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="9a950-132">MRTK ドキュメントホーム</span><span class="sxs-lookup"><span data-stu-id="9a950-132">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="9a950-133">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="9a950-133">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="9a950-134">HTK/MRTK から MRTK バージョン2への移植</span><span class="sxs-lookup"><span data-stu-id="9a950-134">Porting from HTK/MRTK to MRTK version 2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
