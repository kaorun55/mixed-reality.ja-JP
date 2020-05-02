---
title: Unity 開発の概要
description: Unity で Mixed Reality アプリのビルドを開始します。
author: thetuvix
ms.author: kurtie
ms.date: 10/25/2018
ms.topic: article
ms.localizationpriority: high
keywords: Unity, Mixed Reality, 開発, 概要, 新しいプロジェクト, 移植, 機能, カメラ, シミュレーション, エミュレーション, ドキュメント
ms.openlocfilehash: e0fe775f5fe891416145d91e52a5a801e049c568
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "81433418"
---
# <a name="unity-development-overview"></a><span data-ttu-id="924c2-104">Unity 開発の概要</span><span class="sxs-lookup"><span data-stu-id="924c2-104">Unity development overview</span></span>

<span data-ttu-id="924c2-105">[Mixed Reality アプリ](app-views.md)を構築する最速の方法は、[Unity](https://unity.com) を使用することです。</span><span class="sxs-lookup"><span data-stu-id="924c2-105">The fastest path to building a [mixed reality app](app-views.md) is with [Unity](https://unity.com).</span></span> <span data-ttu-id="924c2-106">時間を取って、[Unity のチュートリアル](https://unity3d.com/learn/tutorials)をご覧になることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="924c2-106">We recommend that you take time to explore the [Unity tutorials](https://unity3d.com/learn/tutorials).</span></span> <span data-ttu-id="924c2-107">資産が必要な場合、Unity には包括的な[資産ストア](https://www.assetstore.unity3d.com/)があります。</span><span class="sxs-lookup"><span data-stu-id="924c2-107">If you need assets, Unity has a comprehensive [Asset Store](https://www.assetstore.unity3d.com/).</span></span> <span data-ttu-id="924c2-108">Unity についての基本的な理解ができたら、[チュートリアル](tutorials.md)にアクセスして、Unity を使用した Mixed Reality 開発の詳細を確認できます。</span><span class="sxs-lookup"><span data-stu-id="924c2-108">Once you have built up a basic understanding of Unity, you can visit the [tutorials](tutorials.md) to learn the specifics of mixed reality development with Unity.</span></span> <span data-ttu-id="924c2-109">[Unity Mixed Reality フォーラム](https://forum.unity3d.com/forums/hololens.102/)にアクセスして、Unity で Mixed Reality アプリを構築する他のコミュニティと協働し、遭遇しがちな問題の解決策を見つけてください。</span><span class="sxs-lookup"><span data-stu-id="924c2-109">Be sure to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the rest of the community building mixed reality apps in Unity and find solutions to problems you might run into.</span></span>

<span data-ttu-id="924c2-110">Unity を使用して Mixed Reality アプリの構築を開始するには、まず、[ツールをインストール](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="924c2-110">To get started building mixed reality apps with Unity, first [install the tools](install-the-tools.md).</span></span> 

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Setting-up-your-HoloLens-2-development-environment/player?format=ny]

## <a name="new-unity-project-with-mixed-reality-toolkit"></a><span data-ttu-id="924c2-111">Mixed Reality Toolkit による新しい Unity プロジェクト</span><span class="sxs-lookup"><span data-stu-id="924c2-111">New Unity Project with Mixed Reality Toolkit</span></span> 

<span data-ttu-id="924c2-112">Unity で開発する場合の最も簡単な方法は、Mixed Reality Toolkit を使用することです。</span><span class="sxs-lookup"><span data-stu-id="924c2-112">The easiest way to develop in Unity is with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="924c2-113">これにより、プロジェクトでの設定を自動的に行い、一連の Mixed Reality 機能を提供して開発を促進できます。</span><span class="sxs-lookup"><span data-stu-id="924c2-113">This will help you setup with the project automatically, and provide a set of mixed reality features to accelerate your development.</span></span> <span data-ttu-id="924c2-114">詳細を確認して使い始めるには、[Mixed Reality Toolkit v2](mrtk-getting-started.md) に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="924c2-114">Please check out [Mixed Reality Toolkit v2](mrtk-getting-started.md) to learn more and get started.</span></span> 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a><span data-ttu-id="924c2-115">既存の Unity アプリを Windows Mixed Reality に移植する</span><span class="sxs-lookup"><span data-stu-id="924c2-115">Porting an existing Unity app to Windows Mixed Reality</span></span>

<span data-ttu-id="924c2-116">Windows Mixed Reality への移植を予定している既存の Unity プロジェクトがある場合は、[Unity 移植ガイド](porting-guides.md)に従って作業を開始してください。</span><span class="sxs-lookup"><span data-stu-id="924c2-116">If you have an existing Unity project that you're porting to Windows Mixed Reality, follow along with the [Unity porting guide](porting-guides.md) to get started.</span></span>

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="924c2-117">Windows Mixed Reality 用に新しい Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="924c2-117">Configuring new Unity project for Windows Mixed Reality</span></span>

<span data-ttu-id="924c2-118">Mixed Reality Toolkit をインポートせずに新しい Unity プロジェクトを作成する場合には、Windows Mixed Reality 用に手動で変更する必要がある小規模な Unity 設定のセットがあります。</span><span class="sxs-lookup"><span data-stu-id="924c2-118">If you'd like to create a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality.</span></span> <span data-ttu-id="924c2-119">これらは、プロジェクトごととシーンごとの 2 つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="924c2-119">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="924c2-120">ステップ バイ ステップ ガイドについては、こちらの「[Windows Mixed Reality 用の新しい Unity プロジェクトを構成する](Configure-Unity-Project.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="924c2-120">See here for a step by step guide to [Configure new Unity Project for Windows Mixed Reality](Configure-Unity-Project.md)</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="924c2-121">Mixed Reality の機能と入力値を追加する</span><span class="sxs-lookup"><span data-stu-id="924c2-121">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="924c2-122">プロジェクトに MRTK V2 をセットアップするか、前述のようにプロジェクトを構成したら、標準の Unity ゲーム オブジェクト (カメラなど) が **座位のエクスペリエンス**に対応してすぐに点灯します。ユーザーが頭を移動すると、カメラの位置が自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="924c2-122">Once you've setup MRTK V2 with your project or configured your project as described above, standard Unity game objects (such as the camera) will light up immediately for a **seated-scale experience**, with the camera's position updated automatically as the user moves their head through the world.</span></span>

<span data-ttu-id="924c2-123">Unity に直接組み込まれている API を使用して、[空間ステージ](coordinate-systems.md#spatial-coordinate-systems)、[ジェスチャ、モーション コントローラー](gestures-and-motion-controllers-in-unity.md)、[音声入力](voice-input-in-unity.md)など、Windows Mixed Reality 機能のサポートを追加できます。</span><span class="sxs-lookup"><span data-stu-id="924c2-123">Adding support for Windows Mixed Reality features, such as [spatial stages](coordinate-systems.md#spatial-coordinate-systems), [gestures, motion controllers](gestures-and-motion-controllers-in-unity.md) or [voice input](voice-input-in-unity.md) is achieved using APIs built directly into Unity.</span></span> 

<span data-ttu-id="924c2-124">まず、お使いのアプリケーションが対象にできる[エクスペリエンスのスケール](coordinate-systems.md)を確認します。</span><span class="sxs-lookup"><span data-stu-id="924c2-124">First, review the [experience scales](coordinate-systems.md) that your application can target:</span></span>
* <span data-ttu-id="924c2-125">**向き限定**や**座位のエクスペリエンス**を構築する場合は、Unity 上で追跡する空間の種類を [[ひな形]](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="924c2-125">If you're looking to build an **orientation-only** or **seated-scale experience**, you'll need to set Unity's tracking space type to [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="924c2-126">**立位**または**空間スケールのエクスペリエンス**を構築する場合は、Unity 上で追跡する空間の種類を確実に [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="924c2-126">If you're looking to build a **standing-scale** or **room-scale experience**, you'll need to ensure Unity's tracking space type is successfully set to [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="924c2-127">ユーザーが 5 メートルを超えてローミングできるようにする**ワールドスケール**のエクスペリエンスを HoloLens 上で構築する場合は、[WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) コンポーネントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="924c2-127">If you're looking to build a **world-scale** experience on HoloLens that lets users roam beyond 5 meters, you'll need to use the [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) component.</span></span>

<span data-ttu-id="924c2-128">Mixed Reality アプリケーションのコアな構成要素はすべて、他の Unity API と一貫した手法で公開されています。</span><span class="sxs-lookup"><span data-stu-id="924c2-128">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="924c2-129">また、Mixed Reality Toolkit を通じて入手することもできます。</span><span class="sxs-lookup"><span data-stu-id="924c2-129">They are also available through the Mixed Reality Toolkit.</span></span>
* [<span data-ttu-id="924c2-130">カメラ</span><span class="sxs-lookup"><span data-stu-id="924c2-130">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="924c2-131">座標系</span><span class="sxs-lookup"><span data-stu-id="924c2-131">Coordinate systems</span></span>](coordinate-systems-in-unity.md)
* [<span data-ttu-id="924c2-132">視線入力</span><span class="sxs-lookup"><span data-stu-id="924c2-132">Gaze</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="924c2-133">ジェスチャとモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="924c2-133">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="924c2-134">音声入力</span><span class="sxs-lookup"><span data-stu-id="924c2-134">Voice input</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="924c2-135">永続化</span><span class="sxs-lookup"><span data-stu-id="924c2-135">Persistence</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="924c2-136">立体音響</span><span class="sxs-lookup"><span data-stu-id="924c2-136">Spatial sound</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="924c2-137">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="924c2-137">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="924c2-138">以下に示す、多くの Mixed Reality アプリケーション上で使用される他の重要な機能も、Unity アプリに公開されています。</span><span class="sxs-lookup"><span data-stu-id="924c2-138">There are other key features that many mixed reality applications will want to use that are also exposed to Unity apps:</span></span>
* [<span data-ttu-id="924c2-139">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="924c2-139">Shared experiences</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="924c2-140">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="924c2-140">Locatable camera</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="924c2-141">フォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="924c2-141">Focus point</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="924c2-142">追跡の損失</span><span class="sxs-lookup"><span data-stu-id="924c2-142">Tracking loss</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="924c2-143">キーボード</span><span class="sxs-lookup"><span data-stu-id="924c2-143">Keyboard</span></span>](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a><span data-ttu-id="924c2-144">実際のデバイスまたはシミュレートされたデバイス上で Unity プロジェクトを実行する</span><span class="sxs-lookup"><span data-stu-id="924c2-144">Running your Unity project on a real or simulated device</span></span>

<span data-ttu-id="924c2-145">ホログラフィック Unity プロジェクトをテストする準備ができたら、次の手順として、[Unity Visual Studio ソリューションをエクスポートしてビルド](exporting-and-building-a-unity-visual-studio-solution.md)します。</span><span class="sxs-lookup"><span data-stu-id="924c2-145">Once you've got your holographic Unity project ready for testing, your next step is to [export and build a Unity Visual Studio solution](exporting-and-building-a-unity-visual-studio-solution.md).</span></span>

<span data-ttu-id="924c2-146">その VS ソリューションが手元にあれば、実際のデバイスまたはシミュレートされたデバイスのどちらかを使用して、次の 3 つの方法のいずかでアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="924c2-146">With that VS solution in hand, you can then run your application in one of three ways, using either a real or simulated device:</span></span>
* [<span data-ttu-id="924c2-147">実際の HoloLens または Windows Mixed Reality イマーシブ ヘッドセットにデプロイする</span><span class="sxs-lookup"><span data-stu-id="924c2-147">Deploy to a real HoloLens or Windows Mixed Reality immersive headset</span></span>](using-visual-studio.md)
* [<span data-ttu-id="924c2-148">HoloLens エミュレーターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="924c2-148">Deploy to the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="924c2-149">Windows Mixed Reality イマーシブ ヘッドセット シミュレーターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="924c2-149">Deploy to the Windows Mixed Reality immersive headset simulator</span></span>](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a><span data-ttu-id="924c2-150">Unity のドキュメント</span><span class="sxs-lookup"><span data-stu-id="924c2-150">Unity documentation</span></span>

<span data-ttu-id="924c2-151">このドキュメントは docs.microsoft.com 上で入手できますが、Unity では、Windows Mixed Reality 機能に関するドキュメントが Unity エディターと共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="924c2-151">In addition to this documentation available on docs.microsoft.com, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="924c2-152">Unity が提供するドキュメントには、次の 2 つのセクションがあります。</span><span class="sxs-lookup"><span data-stu-id="924c2-152">The Unity provided documentation includes two separate sections:</span></span>
1. <span data-ttu-id="924c2-153">**Unity スクリプト リファレンス**</span><span class="sxs-lookup"><span data-stu-id="924c2-153">**Unity scripting reference**</span></span>
    * <span data-ttu-id="924c2-154">ドキュメントのこのセクションには、Unity が提供するスクリプト作成 API の詳細が含まれています。</span><span class="sxs-lookup"><span data-stu-id="924c2-154">This section of the documentation contains details of the scripting API that Unity provides.</span></span>
    * <span data-ttu-id="924c2-155">**[ヘルプ] > [Scripting Reference]\(スクリプト作成のリファレンス\)**  を使用して、Unity エディターからアクセス可能です</span><span class="sxs-lookup"><span data-stu-id="924c2-155">Accessible from the Unity Editor through **Help > Scripting Reference**</span></span>
2. <span data-ttu-id="924c2-156">**Unity マニュアル**</span><span class="sxs-lookup"><span data-stu-id="924c2-156">**Unity manual**</span></span>
    * <span data-ttu-id="924c2-157">このマニュアルは、基本的な手法から高度な手法まで、Unity の使用方法を学習できるように編成されています。</span><span class="sxs-lookup"><span data-stu-id="924c2-157">This manual is designed to help you learn how to use Unity, from basic to advanced techniques.</span></span>
    * <span data-ttu-id="924c2-158">**[ヘルプ] > [マニュアル]** を使用して、Unity エディターからアクセス可能です</span><span class="sxs-lookup"><span data-stu-id="924c2-158">Accessible from the Unity Editor through **Help > Manual**</span></span>

## <a name="see-also"></a><span data-ttu-id="924c2-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="924c2-159">See also</span></span>
* [<span data-ttu-id="924c2-160">Mixed Reality Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="924c2-160">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="924c2-161">MR の基本 100:Unity の概要</span><span class="sxs-lookup"><span data-stu-id="924c2-161">MR Basics 100: Getting started with Unity</span></span>](holograms-100.md)
* [<span data-ttu-id="924c2-162">Unity で推奨される設定</span><span class="sxs-lookup"><span data-stu-id="924c2-162">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="924c2-163">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="924c2-163">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="924c2-164">Unity Visual Studio ソリューションのエクスポートとビルド</span><span class="sxs-lookup"><span data-stu-id="924c2-164">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="924c2-165">Windows 名前空間と HoloLens 用 Unity アプリの使用</span><span class="sxs-lookup"><span data-stu-id="924c2-165">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="924c2-166">Unity と Visual Studio を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="924c2-166">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="924c2-167">Unity の再生モード</span><span class="sxs-lookup"><span data-stu-id="924c2-167">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="924c2-168">移植ガイド</span><span class="sxs-lookup"><span data-stu-id="924c2-168">Porting guides</span></span>](porting-guides.md)
