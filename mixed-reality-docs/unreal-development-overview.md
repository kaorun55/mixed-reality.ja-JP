---
title: Unreal 開発の概要
description: Unreal で複合現実アプリのビルドを開始します。
author: sw5813
ms.author: suwu
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4、HoloLens, HoloLens 2, ベータ, ストリーミング, リモート処理, 複合現実, 開発, 使用の開始, 新しいプロジェクト, エミュレーター, ドキュメント
ms.openlocfilehash: 96b0259e4ac567389f999d3a453fb68bb848b266
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "74491170"
---
# <a name="unreal-development-overview"></a><span data-ttu-id="0ee25-104">Unreal 開発の概要</span><span class="sxs-lookup"><span data-stu-id="0ee25-104">Unreal development overview</span></span>

<span data-ttu-id="0ee25-105">Unreal Engine 4 の複合現実のサポートがベータ版になりました。</span><span class="sxs-lookup"><span data-stu-id="0ee25-105">Mixed reality support for Unreal Engine 4 is now in beta!</span></span> <span data-ttu-id="0ee25-106">Unreal での開発を初めて行う場合は、「<a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">UE4 をはじめよう</a>」ページが非常に参考になります。</span><span class="sxs-lookup"><span data-stu-id="0ee25-106">If you're new to Unreal development, <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Getting Started with Unreal Engine 4</a> is a great page to explore.</span></span> <span data-ttu-id="0ee25-107">資産が必要であれば、Unreal には包括的な<a href="https://www.unrealengine.com/marketplace//store" target="_blank">マーケットプレース</a>があります。</span><span class="sxs-lookup"><span data-stu-id="0ee25-107">If you need assets, Unreal has a comprehensive <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a>.</span></span> 

<span data-ttu-id="0ee25-108">Unreal Engine 4 の基本を理解したら、Unreal Engine ドキュメント サイトの「<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens 開発</a>」ページにアクセスして、HoloLens でアプリをビルドして実行する方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="0ee25-108">Once you've built a basic understanding of Unreal Engine 4, you can visit the <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens Development</a> page on the Unreal Engine documentation site to learn how to build and run your apps on HoloLens.</span></span> <span data-ttu-id="0ee25-109"><a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal 複合現実フォーラム</a>にアクセスして、Unreal で複合現実アプリをビルドしているコミュニティに参加してください。</span><span class="sxs-lookup"><span data-stu-id="0ee25-109">Be sure to visit the <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal Mixed Reality forums</a> to engage with the community who build mixed reality apps in Unreal.</span></span> <span data-ttu-id="0ee25-110">それは、発生する可能性のある問題の解決策を見つけるのに最適な場所です。</span><span class="sxs-lookup"><span data-stu-id="0ee25-110">It's a great place to find solutions to problems you might run into.</span></span>

## <a name="installing-the-prerequisites"></a><span data-ttu-id="0ee25-111">必要条件のインストール</span><span class="sxs-lookup"><span data-stu-id="0ee25-111">Installing the prerequisites</span></span>

<span data-ttu-id="0ee25-112">Unreal で HoloLens 2 アプリのビルドを 開始するには、[HoloLens 2 エミュレーター](using-the-hololens-emulator.md)または HoloLens ヘッドセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="0ee25-112">To get started with building a HoloLens 2 app in Unreal, you'll need the [HoloLens 2 Emulator](using-the-hololens-emulator.md) or a HoloLens headset.</span></span> <span data-ttu-id="0ee25-113">さらに、「<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">HoloLens 2 前提条件</a>」に記載されているワークロードとコンポーネントを備えた最新バージョンの Visual Studio をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ee25-113">You'll also need to install the latest version of Visual Studio with the workloads and components listed in <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">HoloLens 2 Prerequisites for Unreal</a>.</span></span>

## <a name="building-and-running-your-unreal-app"></a><span data-ttu-id="0ee25-114">Unreal アプリのビルドと実行</span><span class="sxs-lookup"><span data-stu-id="0ee25-114">Building and running your Unreal app</span></span>

<span data-ttu-id="0ee25-115">最初に、<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">アプリを HoloLens 2 用にパッケージ化</a>します。</span><span class="sxs-lookup"><span data-stu-id="0ee25-115">First, <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">package your app for HoloLens 2</a>.</span></span> <span data-ttu-id="0ee25-116">次に、パッケージのデプロイ先を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ee25-116">Next, choose where you want to deploy your package:</span></span>
* <span data-ttu-id="0ee25-117"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">HoloLens 2 エミュレーターにデプロイする</a></span><span class="sxs-lookup"><span data-stu-id="0ee25-117"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">Deploy to the HoloLens 2 Emulator</a></span></span>
* <span data-ttu-id="0ee25-118"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">HoloLens 2 ヘッドセットにデプロイする</a></span><span class="sxs-lookup"><span data-stu-id="0ee25-118"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">Deploy to a HoloLens 2 Headset</a></span></span>

## <a name="streaming-your-app-to-a-headset-via-the-holographic-remoting-player"></a><span data-ttu-id="0ee25-119">ホログラフィック リモート プレーヤー経由のヘッドセットへのアプリのストリーミング</span><span class="sxs-lookup"><span data-stu-id="0ee25-119">Streaming your app to a headset via the Holographic Remoting Player</span></span>

<span data-ttu-id="0ee25-120">デスクトップから HoloLens ヘッドセット上の Holographic Remoting Player アプリへのアプリのストリーミングには、2 つの大きなメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="0ee25-120">Streaming your app from your desktop to the Holographic Remoting Player app on a HoloLens headset has two main advantages:</span></span> 
* <span data-ttu-id="0ee25-121">開発が高速化されます。このため、変更を加えるたびにアプリを再パッケージ化してアップロードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0ee25-121">Speeds up development, so there's no need to repackage and upload your app each time you make a change</span></span>
* <span data-ttu-id="0ee25-122">デスクトップのパワーが活用されます。このため、ヘッドセットで利用できるコンピューターによる制限を受けずに、デスクトップの GPU で許可されるだけの数のポリゴンをレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="0ee25-122">Leverages the power of your desktop, so you can render as many polygons as your desktop GPU allows, without being limited by the computer available on the headset</span></span>

<span data-ttu-id="0ee25-123">ストリーミングの使用を開始するには、「<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2 ストリーミングのクイック スタート</a>[]()」をご確認ください。</span><span class="sxs-lookup"><span data-stu-id="0ee25-123">To get started with streaming, check out the <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2 Streaming Quick Start</a>[]().</span></span>

## <a name="see-also"></a><span data-ttu-id="0ee25-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ee25-124">See also</span></span>
* <span data-ttu-id="0ee25-125"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">モバイル デバイスのパフォーマンス ガイドライン (Unreal)</a></span><span class="sxs-lookup"><span data-stu-id="0ee25-125"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Unreal performance guidelines for mobile devices</a></span></span>
