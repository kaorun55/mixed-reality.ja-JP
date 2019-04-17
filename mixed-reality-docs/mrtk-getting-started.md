---
title: MRTK バージョン 2 の概要
description: 新しい開発者 MRTK を活用することに関心が向け
author: grbury
ms.author: grbury
ms.date: 02/22/19
ms.topic: article
keywords: Windows Mixed Reality、テスト、MRTK バージョン 2、MRTK、ツール、SDK、HoloLens、HoloLens 2
ms.openlocfilehash: 44e5fe0fd4384af68922eda4bcb0594d39a1c1b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600031"
---
# <a name="getting-started-with-mrtk-version-2"></a><span data-ttu-id="fce8c-104">MRTK バージョン 2 の概要</span><span class="sxs-lookup"><span data-stu-id="fce8c-104">Getting started with MRTK version 2</span></span>

<span data-ttu-id="fce8c-105">MRTK は、HoloLens はリリース当初とでは、今せずに作成した開発者コミュニティの困難な作業はできないためにきました驚くようなオープン ソースのツールキットです。</span><span class="sxs-lookup"><span data-stu-id="fce8c-105">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="fce8c-106">過去 3 年の間、開発者コミュニティのフィードバックに応えし、する最大の懸念事項を考慮に入れて MRTK バージョン 2 を構築しました。</span><span class="sxs-lookup"><span data-stu-id="fce8c-106">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK version 2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="fce8c-107">Unity を使った MRTK バージョン 2 は、複合現実のアプリケーション用のオープン ソース クロス プラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="fce8c-107">The MRTK version 2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="fce8c-108">MRTK バージョン 2 の目的は、Microsoft HoloLens、Windows Mixed Reality 没入型 (VR) ヘッドセットと OpenVR プラットフォームを対象とするアプリケーションの開発を促進します。</span><span class="sxs-lookup"><span data-stu-id="fce8c-108">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="fce8c-109">プロジェクトの目的は、複合現実のアプリケーションを作成しすべての拡大に伴い、コミュニティに貢献するエントリに対する障壁を削減です。</span><span class="sxs-lookup"><span data-stu-id="fce8c-109">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="fce8c-110">参照してください、 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Getting-Started-with-MRTK-v2" target="_blank">MRTK バージョン 2 の wiki</a>概要および詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="fce8c-110">See the <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Getting-Started-with-MRTK-v2" target="_blank">MRTK version 2 wiki</a> to get started and learn more.</span></span>

## <a name="new-with-mrtk-version-2"></a><span data-ttu-id="fce8c-111">MRTK バージョン 2 で新しい</span><span class="sxs-lookup"><span data-stu-id="fce8c-111">New with MRTK version 2</span></span>
<span data-ttu-id="fce8c-112">これらのプラットフォーム ツールに対するマイクロソフトのコミットメントを強調します。</span><span class="sxs-lookup"><span data-stu-id="fce8c-112">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="fce8c-113">実際には、セットアップ experience (OOBE) や Mixed Reality Learning アプリケーションなど、受信トレイ エクスペリエンスを開発する MRTK バージョン 2 を利用します。</span><span class="sxs-lookup"><span data-stu-id="fce8c-113">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="fce8c-114">最初は、プラットフォーム上で開発する最善の方法を考えているためです MRTK を通じて公開されている新しい HoloLens 2 機能を確認することも期待できます。</span><span class="sxs-lookup"><span data-stu-id="fce8c-114">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="fce8c-115">モジュール</span><span class="sxs-lookup"><span data-stu-id="fce8c-115">Modular</span></span>
<span data-ttu-id="fce8c-116">ツールキットのすべてのビットをプロジェクトを考慮する必要はありませんようにして、モジュール方式で作成しましたがあります。</span><span class="sxs-lookup"><span data-stu-id="fce8c-116">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="fce8c-117">これを実際には、いくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="fce8c-117">There are actually a few benefits to this.</span></span>  <span data-ttu-id="fce8c-118">プロジェクトのサイズを小さく維持だけでなく管理しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="fce8c-118">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="fce8c-119">スクリプト可能なオブジェクトで構築されていますので、インターフェイス駆動ことも、その他のサービス、システム、およびプラットフォームをサポートするために、独自に含まれているコンポーネントを交換するため。</span><span class="sxs-lookup"><span data-stu-id="fce8c-119">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="fce8c-120">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="fce8c-120">Cross-platform</span></span>
<span data-ttu-id="fce8c-121">その他のプラットフォームと言えば、クロス プラットフォーム サポートしています。</span><span class="sxs-lookup"><span data-stu-id="fce8c-121">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="fce8c-122">すべて 1 つのプラットフォームがサポートしているわけでは中、に他のプラットフォーム、ビルド ターゲットを切り替えたときに中断されます toolkit のことを確認されました。</span><span class="sxs-lookup"><span data-stu-id="fce8c-122">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="fce8c-123">堅牢性とモジュールの設計による拡張機能を ARCore、ARKit、OpenVR など、複数のプラットフォームをサポートできる適切なパスを設定します。</span><span class="sxs-lookup"><span data-stu-id="fce8c-123">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="fce8c-124">パフォーマンスの高い</span><span class="sxs-lookup"><span data-stu-id="fce8c-124">Performant</span></span>
<span data-ttu-id="fce8c-125">モバイル プラットフォームを使用 20050607 がパフォーマンスに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fce8c-125">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="fce8c-126">これは非常に重要なツールが働きますしようとしていないことを確認したいです。</span><span class="sxs-lookup"><span data-stu-id="fce8c-126">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="fce8c-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="fce8c-127">See also</span></span>
* [<span data-ttu-id="fce8c-128">ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="fce8c-128">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="fce8c-129">HTK/MRTK から MRTK バージョン 2 への移植</span><span class="sxs-lookup"><span data-stu-id="fce8c-129">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)
