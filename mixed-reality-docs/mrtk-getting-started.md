---
title: MRTK バージョン2の概要
description: MRTK の活用に関心がある新しい開発者向け
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
keywords: Windows Mixed Reality、test、Mixed Reality Toolkit、MRTK バージョン2、MRTK、tools、SDK、HoloLens、HoloLens 2
ms.openlocfilehash: bb958543aa68586dd689a2048665b233d6be7064
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913128"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="ae8ed-104">MRTK v2 の概要</span><span class="sxs-lookup"><span data-stu-id="ae8ed-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="ae8ed-105">MRTK はじめにガイド</span><span class="sxs-lookup"><span data-stu-id="ae8ed-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="ae8ed-106">MRTK V2 の概要については、「 [mrtk ファーストステップガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for detailed information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="ae8ed-107">Mixed Reality Toolkit (MRTK) とは</span><span class="sxs-lookup"><span data-stu-id="ae8ed-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="ae8ed-108">MRTK は、HoloLens が最初にリリースされた後に行われていたすばらしいオープンソースのツールキットであり、現在のところ、開発者コミュニティが提供されているので、このツールキットを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="ae8ed-109">過去3年間、microsoft は開発者コミュニティのフィードバックを受け、最大の関心事を考慮するために MRTK v2 を構築しました。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="ae8ed-110">Unity での MRTK v2 は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="ae8ed-111">MRTK バージョン 2 は、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="ae8ed-112">プロジェクトは、参加する障壁を減らすことを目的としています。これにより、複雑な現実アプリケーションを作成し、すべての拡大に応じてコミュニティに貢献できます。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-112">The project is aimed at reducing barriers to entry, to create mixed reality applications and contribute back to the community as we all grow.</span></span> 

<span data-ttu-id="ae8ed-113">詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="ae8ed-114">MRTK v2 の新バージョン</span><span class="sxs-lookup"><span data-stu-id="ae8ed-114">New with MRTK v2</span></span>
<span data-ttu-id="ae8ed-115">これらのプラットフォームツールに対するコミットメントを重視したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-115">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="ae8ed-116">実際、MRTK バージョン2を利用して、setup experience (OOBE) や Mixed Reality Learning アプリケーションなどの受信トレイエクスペリエンスを開発しました。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-116">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="ae8ed-117">また、プラットフォームで開発するのに最適な方法であると考えられるため、新しい HoloLens 2 機能が MRTK を通じて最初に公開されることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-117">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="ae8ed-118">方式</span><span class="sxs-lookup"><span data-stu-id="ae8ed-118">Modular</span></span>
<span data-ttu-id="ae8ed-119">モジュール型の方法でビルドしたので、ツールキットのすべての機能をプロジェクトに組み込む必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-119">We have built it in a modular way, so there's no need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="ae8ed-120">これには、実際にいくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-120">There are actually a few benefits to this.</span></span>  <span data-ttu-id="ae8ed-121">これにより、プロジェクトのサイズが小さくなり、管理が容易になります。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-121">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="ae8ed-122">さらに、スクリプト可能なオブジェクトを使用して構築され、インターフェイス主導型であるため、独自のに含まれているコンポーネントを置き換えることで、他のサービス、システム、およびプラットフォームをサポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-122">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="ae8ed-123">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="ae8ed-123">Cross-platform</span></span>
<span data-ttu-id="ae8ed-124">他のプラットフォームの場合は、クロスプラットフォームのサポートがあります。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-124">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="ae8ed-125">これは、すべての単一プラットフォームが既定でサポートされているわけではありませんが、ビルドターゲットを他のプラットフォームに切り替えると、どのツールキットコードも破損しないようにしました。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-125">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="ae8ed-126">モジュール型の設計による堅牢性と拡張性により、ARCore、Arcore、OpenVR などの複数のプラットフォームをサポートするための優れたパスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-126">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="ae8ed-127">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="ae8ed-127">Performant</span></span>
<span data-ttu-id="ae8ed-128">モバイルプラットフォームを使用すると、パフォーマンスを考慮して構築されています。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-128">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="ae8ed-129">これは非常に重要であり、ツールがお客様に対して機能しないようにする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="ae8ed-129">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae8ed-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae8ed-130">See also</span></span>
* [<span data-ttu-id="ae8ed-131">MRTK ファーストステップガイド</span><span class="sxs-lookup"><span data-stu-id="ae8ed-131">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="ae8ed-132">MRTK ドキュメントホーム</span><span class="sxs-lookup"><span data-stu-id="ae8ed-132">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="ae8ed-133">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="ae8ed-133">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="ae8ed-134">HTK/MRTK から MRTK バージョン2への移植</span><span class="sxs-lookup"><span data-stu-id="ae8ed-134">Porting from HTK/MRTK to MRTK version 2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
