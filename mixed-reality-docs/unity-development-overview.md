---
title: Unity 開発の概要
description: Unity での mixed reality アプリの構築の概要。
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, mixed reality, 開発, 作業の開始, 新しいプロジェクト, 移植, 機能, カメラ, シミュレーション, エミュレーション, ドキュメント
ms.openlocfilehash: b1384e886a2b4d0b3ed9f8008fca6af6ad4b78d5
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701790"
---
# <a name="unity-development-overview"></a><span data-ttu-id="def74-104">Unity 開発の概要</span><span class="sxs-lookup"><span data-stu-id="def74-104">Unity development overview</span></span>

<span data-ttu-id="def74-105">[Mixed reality アプリ](app-views.md)を構築する最速のパスは、 [Unity](http://aka.ms/HoloLensUnity)を使用することです。</span><span class="sxs-lookup"><span data-stu-id="def74-105">The fastest path to building a [mixed reality app](app-views.md) is with [Unity](http://aka.ms/HoloLensUnity).</span></span> <span data-ttu-id="def74-106">[Unity のチュートリアル](https://unity3d.com/learn/tutorials)をご覧になることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="def74-106">We recommend that you take time to explore the [Unity tutorials](https://unity3d.com/learn/tutorials).</span></span> <span data-ttu-id="def74-107">資産が必要な場合、Unity には包括的な[資産ストア](https://www.assetstore.unity3d.com/)があります。</span><span class="sxs-lookup"><span data-stu-id="def74-107">If you need assets, Unity has a comprehensive [Asset Store](https://www.assetstore.unity3d.com/).</span></span> <span data-ttu-id="def74-108">Unity についての基本的な理解を構築したら、[チュートリアル](tutorials.md)にアクセスして unity を使用した mixed reality 開発の詳細を学習できます。</span><span class="sxs-lookup"><span data-stu-id="def74-108">Once you have built up a basic understanding of Unity, you can visit the [tutorials](tutorials.md) to learn the specifics of mixed reality development with Unity.</span></span> <span data-ttu-id="def74-109">Unity で mixed reality アプリを構築するその他のコミュニティと連携するには、 [Unity Mixed reality フォーラム](http://forum.unity3d.com/forums/hololens.102/)にアクセスし、発生する可能性のある問題の解決策を見つけてください。</span><span class="sxs-lookup"><span data-stu-id="def74-109">Be sure to visit the [Unity Mixed Reality forums](http://forum.unity3d.com/forums/hololens.102/) to engage with the rest of the community building mixed reality apps in Unity and find solutions to problems you might run into.</span></span>

<span data-ttu-id="def74-110">Unity を使用した mixed reality アプリの構築を開始するには、まず[ツールをインストール](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="def74-110">To get started building mixed reality apps with Unity, first [install the tools](install-the-tools.md).</span></span> 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a><span data-ttu-id="def74-111">Mixed Reality Toolkit を使用した新しい Unity プロジェクト</span><span class="sxs-lookup"><span data-stu-id="def74-111">New Unity Project with Mixed Reality Toolkit</span></span> 

<span data-ttu-id="def74-112">Unity で開発する最も簡単な方法は、Mixed Reality Toolkit を使用することです。</span><span class="sxs-lookup"><span data-stu-id="def74-112">The easiest way to develop in Unity is with the help of Mixed Reality Toolkit.</span></span> <span data-ttu-id="def74-113">これは、プロジェクトを自動的に設定し、開発を加速させる一連の mixed reality 機能を提供するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="def74-113">It will help you setup with project automatically, and provide a set of mixed reality features to accelerate your development.</span></span> <span data-ttu-id="def74-114">詳細については、「 [Mixed Reality Toolkit v2](mrtk-getting-started.md) 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="def74-114">Please check out [Mixed Reality Toolkit v2](mrtk-getting-started.md) to learn more and get started.</span></span> 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a><span data-ttu-id="def74-115">既存の Unity アプリを Windows Mixed Reality に移植する</span><span class="sxs-lookup"><span data-stu-id="def74-115">Porting an existing Unity app to Windows Mixed Reality</span></span>

<span data-ttu-id="def74-116">Windows Mixed Reality に移植している既存の Unity プロジェクトがある場合は、 [unity の移植](porting-guides.md)に関するガイドに従って作業を開始してください。</span><span class="sxs-lookup"><span data-stu-id="def74-116">If you have an existing Unity project that you're porting to Windows Mixed Reality, follow along with the [Unity porting guide](porting-guides.md) to get started.</span></span>

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="def74-117">Windows Mixed Reality 用の新しい Unity プロジェクトの構成</span><span class="sxs-lookup"><span data-stu-id="def74-117">Configuring new Unity project for Windows Mixed Reality</span></span>

<span data-ttu-id="def74-118">混合 Reality ツールキットをインポートせずに新しい Unity プロジェクトを作成する場合は、Windows Mixed Reality で手動で変更する必要がある Unity 設定の小さなセットがあります。</span><span class="sxs-lookup"><span data-stu-id="def74-118">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality.</span></span> <span data-ttu-id="def74-119">これらは、プロジェクトごととシーン単位の2つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="def74-119">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="def74-120">[Windows Mixed Reality 用の新しい Unity プロジェクトを構成](Configure-Unity-Project.md)するためのステップバイステップガイドについては、こちらをご覧ください</span><span class="sxs-lookup"><span data-stu-id="def74-120">See here for step by step guide to [Configure new Unity Project for Windows Mixed Reality](Configure-Unity-Project.md)</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="def74-121">Mixed reality 機能と入力の追加</span><span class="sxs-lookup"><span data-stu-id="def74-121">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="def74-122">プロジェクトで MRTK V2 を設定した後、または前述のようにプロジェクトを構成した後、標準 Unity ゲームオブジェクト (カメラなど) は、挿入された**スケールエクスペリエンス**のためにすぐに点灯します。カメラの位置は、ユーザーは、世界中を移動します。</span><span class="sxs-lookup"><span data-stu-id="def74-122">Once you've setup MRTK V2 with your project, or configured your project as described above, standard Unity game objects (such as the camera) will light up immediately for a **seated-scale experience**, with the camera's position updated automatically as the user moves their head through the world.</span></span>

<span data-ttu-id="def74-123">[空間ステージ](coordinate-systems.md#spatial-coordinate-systems)、[ジェスチャ、モーションコントローラー](gestures-and-motion-controllers-in-unity.md) 、[音声入力](voice-input-in-unity.md)など、Windows Mixed Reality 機能のサポートを追加するには、Unity に直接組み込まれている api を使用します。</span><span class="sxs-lookup"><span data-stu-id="def74-123">Adding support for Windows Mixed Reality features, such as [spatial stages](coordinate-systems.md#spatial-coordinate-systems), [gestures, motion controllers](gestures-and-motion-controllers-in-unity.md) or [voice input](voice-input-in-unity.md) is achieved using APIs built directly into Unity.</span></span> 

<span data-ttu-id="def74-124">まず、アプリケーションが対象とする[エクスペリエンススケール](coordinate-systems.md)を確認します。</span><span class="sxs-lookup"><span data-stu-id="def74-124">First, review the [experience scales](coordinate-systems.md) that your applicatioin can target:</span></span>
* <span data-ttu-id="def74-125">**向きのみ**または取り付けられた**スケールエクスペリエンス**を構築しようとしている場合は、Unity の追跡領域の種類を [[固定](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)] に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="def74-125">If you're looking to build an **orientation-only** or **seated-scale experience**, you'll need to set Unity's tracking space type to [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="def74-126">継続**スケール**または**ルームスケールのエクスペリエンス**を構築しようとしている場合は、Unity の追跡領域の種類が正常に[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="def74-126">If you're looking to build a **standing-scale** or **room-scale experience**, you'll need to ensure Unity's tracking space type is successfully set to [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="def74-127">ユーザーが5メートルを超えてローミングできるようにするために、HoloLens で**世界規模**のエクスペリエンスを構築する場合は、 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)コンポーネントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="def74-127">If you're looking to build a **world-scale** experience on HoloLens that lets users roam beyond 5 meters, you'll need to use the [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) component.</span></span>

<span data-ttu-id="def74-128">Mixed reality アプリケーションのすべてのコア構成要素は、他の Unity Api と一貫性のある方法で公開されます。</span><span class="sxs-lookup"><span data-stu-id="def74-128">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="def74-129">これらは、Mixed Reality Toolkit を通じて入手することもできます。</span><span class="sxs-lookup"><span data-stu-id="def74-129">They are also available through the Mixed Reality Toolkit.</span></span>
* [<span data-ttu-id="def74-130">カメラ</span><span class="sxs-lookup"><span data-stu-id="def74-130">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="def74-131">座標系</span><span class="sxs-lookup"><span data-stu-id="def74-131">Coordinate systems</span></span>](coordinate-systems-in-unity.md)
* [<span data-ttu-id="def74-132">視線入力</span><span class="sxs-lookup"><span data-stu-id="def74-132">Gaze</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="def74-133">ジェスチャとモーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="def74-133">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="def74-134">音声入力</span><span class="sxs-lookup"><span data-stu-id="def74-134">Voice input</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="def74-135">永続性</span><span class="sxs-lookup"><span data-stu-id="def74-135">Persistence</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="def74-136">立体音響</span><span class="sxs-lookup"><span data-stu-id="def74-136">Spatial sound</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="def74-137">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="def74-137">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="def74-138">Unity アプリにも公開されている多くの mixed reality アプリケーションでは、次のような重要な機能が使用されます。</span><span class="sxs-lookup"><span data-stu-id="def74-138">There are other key features that many mixed reality applications will want to use that are also exposed to Unity apps:</span></span>
* [<span data-ttu-id="def74-139">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="def74-139">Shared experiences</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="def74-140">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="def74-140">Locatable camera</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="def74-141">フォーカスポイント</span><span class="sxs-lookup"><span data-stu-id="def74-141">Focus point</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="def74-142">損失の追跡</span><span class="sxs-lookup"><span data-stu-id="def74-142">Tracking loss</span></span>](tracking-loss-in-unity.md)
* <span data-ttu-id="def74-143">[[キーボード]](keyboard-input-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="def74-143">[Keyboard](keyboard-input-in-unity.md)</span></span>

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a><span data-ttu-id="def74-144">実際のデバイスまたはシミュレートされたデバイスで Unity プロジェクトを実行する</span><span class="sxs-lookup"><span data-stu-id="def74-144">Running your Unity project on a real or simulated device</span></span>

<span data-ttu-id="def74-145">Holographic Unity プロジェクトをテストする準備ができたら、次の手順として、 [Unity Visual Studio ソリューションをエクスポートしてビルド](exporting-and-building-a-unity-visual-studio-solution.md)します。</span><span class="sxs-lookup"><span data-stu-id="def74-145">Once you've got your holographic Unity project ready for testing, your next step is to [export and build a Unity Visual Studio solution](exporting-and-building-a-unity-visual-studio-solution.md).</span></span>

<span data-ttu-id="def74-146">この VS ソリューションを使用すると、実際のデバイスまたはシミュレートされたデバイスのいずれかを使用して、次の3つの方法のいずれかでアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="def74-146">With that VS solution in hand, you can then run your application in one of three ways, using either a real or simulated device:</span></span>
* [<span data-ttu-id="def74-147">Real HoloLens または Windows Mixed Reality の、イマーシブヘッドセットへのデプロイ</span><span class="sxs-lookup"><span data-stu-id="def74-147">Deploy to a real HoloLens or Windows Mixed Reality immersive headset</span></span>](using-visual-studio.md)
* [<span data-ttu-id="def74-148">HoloLens エミュレーターへのデプロイ</span><span class="sxs-lookup"><span data-stu-id="def74-148">Deploy to the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="def74-149">Windows Mixed Reality のイマーシブヘッドセットシミュレーターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="def74-149">Deploy to the Windows Mixed Reality immersive headset simulator</span></span>](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a><span data-ttu-id="def74-150">Unity のドキュメント</span><span class="sxs-lookup"><span data-stu-id="def74-150">Unity documentation</span></span>

<span data-ttu-id="def74-151">Unity では、docs.microsoft.com で提供されているこのドキュメントに加えて、Unity エディターと共に Windows Mixed Reality 機能に関するドキュメントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="def74-151">In addition to this documentation available on docs.microsoft.com, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="def74-152">Unity が提供するドキュメントには、次の2つのセクションがあります。</span><span class="sxs-lookup"><span data-stu-id="def74-152">The Unity provided documentation includes two separate sections:</span></span>
1. <span data-ttu-id="def74-153">**Unity スクリプトリファレンス**</span><span class="sxs-lookup"><span data-stu-id="def74-153">**Unity scripting reference**</span></span>
    * <span data-ttu-id="def74-154">ドキュメントのこのセクションには、Unity が提供するスクリプト API の詳細が含まれています。</span><span class="sxs-lookup"><span data-stu-id="def74-154">This section of the documentation contains details of the scripting API that Unity provides.</span></span>
    * <span data-ttu-id="def74-155">**ヘルプ > スクリプト参照**を使用して Unity エディターからアクセス可能</span><span class="sxs-lookup"><span data-stu-id="def74-155">Accessible from the Unity Editor through **Help > Scripting Reference**</span></span>
2. <span data-ttu-id="def74-156">**Unity マニュアル**</span><span class="sxs-lookup"><span data-stu-id="def74-156">**Unity manual**</span></span>
    * <span data-ttu-id="def74-157">このマニュアルは、基本的な手法から高度な手法まで、Unity の使用方法を学習できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="def74-157">This manual is designed to help you learn how to use Unity, from basic to advanced techniques.</span></span>
    * <span data-ttu-id="def74-158">**ヘルプ > 手動**で、Unity エディターからアクセス可能</span><span class="sxs-lookup"><span data-stu-id="def74-158">Accessible from the Unity Editor through **Help > Manual**</span></span>

## <a name="see-also"></a><span data-ttu-id="def74-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="def74-159">See also</span></span>
* [<span data-ttu-id="def74-160">Mixed Reality Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="def74-160">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="def74-161">MR の基本 100:Unity の概要</span><span class="sxs-lookup"><span data-stu-id="def74-161">MR Basics 100: Getting started with Unity</span></span>](holograms-100.md)
* [<span data-ttu-id="def74-162">Unity で推奨される設定</span><span class="sxs-lookup"><span data-stu-id="def74-162">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="def74-163">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="def74-163">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="def74-164">Unity Visual Studio ソリューションのエクスポートとビルド</span><span class="sxs-lookup"><span data-stu-id="def74-164">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="def74-165">Windows 名前空間と HoloLens 用 Unity アプリの使用</span><span class="sxs-lookup"><span data-stu-id="def74-165">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="def74-166">Unity と Visual Studio を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="def74-166">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="def74-167">Unity の再生モード</span><span class="sxs-lookup"><span data-stu-id="def74-167">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="def74-168">移植のガイド</span><span class="sxs-lookup"><span data-stu-id="def74-168">Porting guides</span></span>](porting-guides.md)
