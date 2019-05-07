---
title: Unity 開発の概要
description: 構築の作業開始の複合現実アプリ Unity でします。
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity では、実際には、開発、作業の開始、新しいプロジェクト、移植、機能、カメラ、シミュレーション、エミュレーション、ドキュメントの混在
ms.openlocfilehash: 2cdcd5e997ab7e3f6d340377464e453a8e7c025c
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64874001"
---
# <a name="unity-development-overview"></a><span data-ttu-id="82e73-104">Unity 開発の概要</span><span class="sxs-lookup"><span data-stu-id="82e73-104">Unity development overview</span></span>

<span data-ttu-id="82e73-105">最も高速パスのビルド方法、 [mixed reality アプリ](app-views.md)は[Unity](http://aka.ms/HoloLensUnity)。</span><span class="sxs-lookup"><span data-stu-id="82e73-105">The fastest path to building a [mixed reality app](app-views.md) is with [Unity](http://aka.ms/HoloLensUnity).</span></span> <span data-ttu-id="82e73-106">探索する時間を取ることをお勧めします。、 [Unity チュートリアル](https://unity3d.com/learn/tutorials)します。</span><span class="sxs-lookup"><span data-stu-id="82e73-106">We recommend you take the time to explore the [Unity tutorials](https://unity3d.com/learn/tutorials).</span></span> <span data-ttu-id="82e73-107">Unity が包括的で資産が必要な場合[Asset Store](https://www.assetstore.unity3d.com/)します。</span><span class="sxs-lookup"><span data-stu-id="82e73-107">If you need assets, Unity has a comprehensive [Asset Store](https://www.assetstore.unity3d.com/).</span></span> <span data-ttu-id="82e73-108">アクセスすることができます、Unity の基本的な知識を蓄積した後、[チュートリアル](tutorials.md)を Unity での複合現実開発の詳細を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82e73-108">Once you have built up a basic understanding of Unity, you can visit the [tutorials](tutorials.md) to learn the specifics of mixed reality development with Unity.</span></span> <span data-ttu-id="82e73-109">参照してください、 [Unity Mixed Reality フォーラム](http://forum.unity3d.com/forums/hololens.102/)が発生する問題の解決策を見つけて、コミュニティの構築、Unity での複合現実アプリの残りの部分とかかわります。</span><span class="sxs-lookup"><span data-stu-id="82e73-109">Be sure to visit the [Unity Mixed Reality forums](http://forum.unity3d.com/forums/hololens.102/) to engage with the rest of the community building mixed reality apps in Unity and find solutions to problems you might run into.</span></span>


<span data-ttu-id="82e73-110">まず、Unity を使用した複合現実アプリの構築を開始する[ツールをインストールする](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="82e73-110">To get started building mixed reality apps with Unity, first [install the tools](install-the-tools.md).</span></span> 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a><span data-ttu-id="82e73-111">Mixed Reality ツールキットを使用して新しい Unity プロジェクト</span><span class="sxs-lookup"><span data-stu-id="82e73-111">New Unity Project with Mixed Reality Toolkit</span></span> 

<span data-ttu-id="82e73-112">Unity での開発に最も簡単な方法は、Mixed Reality ツールキットのヘルプです。</span><span class="sxs-lookup"><span data-stu-id="82e73-112">The easiest way to develop in Unity is with the help of Mixed Reality Toolkit.</span></span> <span data-ttu-id="82e73-113">プロジェクトのセットアップのヘルプを自動的に、一連の開発を促進する Mixed Reality 機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="82e73-113">It will help you setup with project automatically, and provide a set of Mixed Reality features to accelerate your development.</span></span> <span data-ttu-id="82e73-114">チェック アウトしてください[Mixed Reality Toolkit v2](mrtk-getting-started.md)詳細と開始します。</span><span class="sxs-lookup"><span data-stu-id="82e73-114">Please check out [Mixed Reality Toolkit v2](mrtk-getting-started.md) to learn more and get started.</span></span> 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a><span data-ttu-id="82e73-115">Windows Mixed Reality への既存の Unity アプリの移植</span><span class="sxs-lookup"><span data-stu-id="82e73-115">Porting an existing Unity app to Windows Mixed Reality</span></span>

<span data-ttu-id="82e73-116">Windows Mixed Reality を移植する既存の Unity プロジェクトを使用する場合はと共にに従って、 [Unity 移植のガイド](porting-guides.md)を開始します。</span><span class="sxs-lookup"><span data-stu-id="82e73-116">If you have an existing Unity project that you're porting to Windows Mixed Reality, follow along with the [Unity porting guide](porting-guides.md) to get started.</span></span>

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="82e73-117">新しい Unity プロジェクトを Windows Mixed Reality の構成</span><span class="sxs-lookup"><span data-stu-id="82e73-117">Configuring new Unity project for Windows Mixed Reality</span></span>

<span data-ttu-id="82e73-118">Mixed Reality ツールキットをインポートせず、新しい Unity プロジェクトを作成したい場合は、少数の Unity の設定が 2 つのカテゴリに分類、Windows Mixed Reality を手動で変更する必要があります。 プロジェクトごとおよびシーンごと。</span><span class="sxs-lookup"><span data-stu-id="82e73-118">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality, broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="82e73-119">ステップ バイ ステップ ガイドについてはこちらを参照してください[新しい Unity プロジェクトの Windows Mixed Reality を構成する。](Configure-Unity-Project.md)</span><span class="sxs-lookup"><span data-stu-id="82e73-119">See here for step by step guide to [Configure new Unity Project for Windows Mixed Reality](Configure-Unity-Project.md)</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="82e73-120">複合現実の機能および入力の追加</span><span class="sxs-lookup"><span data-stu-id="82e73-120">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="82e73-121">プロジェクトとセットアップ MRTK V2 をしたか、前述のように、プロジェクトを構成すると、(カメラ) などの標準の Unity ゲーム オブジェクトが点灯直後の**取り付けられているスケール エクスペリエンス**カメラの位置を更新自動的にユーザーとして、世界中から自分の頭に移動します。</span><span class="sxs-lookup"><span data-stu-id="82e73-121">Once you've setup MRTK V2 with your project, or configured your project as described above, standard Unity game objects (such as the camera) will light up immediately for a **seated-scale experience**, with the camera's position updated automatically as the user moves their head through the world.</span></span>

<span data-ttu-id="82e73-122">Windows Mixed Reality 機能のサポートを追加するなど、[空間ステージ](coordinate-systems.md#spatial-coordinate-systems)、[ジェスチャ、モーションのコント ローラー](gestures-and-motion-controllers-in-unity.md)または[音声入力](voice-input-in-unity.md)に直接組み込まれている Api を使用して実現されますUnity です。</span><span class="sxs-lookup"><span data-stu-id="82e73-122">Adding support for Windows Mixed Reality features such as [spatial stages](coordinate-systems.md#spatial-coordinate-systems), [gestures, motion controllers](gestures-and-motion-controllers-in-unity.md) or [voice input](voice-input-in-unity.md) is achieved using APIs built directly into Unity.</span></span> 

<span data-ttu-id="82e73-123">最初の手順は、確認する必要があります、[スケールが発生する](coordinate-systems.md)アプリを対象とします。</span><span class="sxs-lookup"><span data-stu-id="82e73-123">Your first step should be to review the [experience scales](coordinate-systems.md) that your app can target:</span></span>
* <span data-ttu-id="82e73-124">ビルドに必要な場合、**向き専用**または**取り付けられているスケール エクスペリエンス**、設定する必要があります Unity に領域の種類の追跡の[静止](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="82e73-124">If you're looking to build an **orientation-only** or **seated-scale experience**, you'll need to set Unity's tracking space type to [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="82e73-125">ビルドに必要な場合、**継続スケール**または**ルーム スケール エクスペリエンス**、Unity のことを確認する必要がありますに正常に設定されて領域の種類を追跡[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)します。</span><span class="sxs-lookup"><span data-stu-id="82e73-125">If you're looking to build a **standing-scale** or **room-scale experience**, you'll need to ensure Unity's tracking space type is successfully set to [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="82e73-126">ビルドに必要な場合、**世界規模**、HoloLens でエクスペリエンスをユーザーが 5 m を超えるローミングできるようにすることを使用する必要があります、 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="82e73-126">If you're looking to build a **world-scale** experience on HoloLens, letting users roam beyond 5 meters, you'll need to use the [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) component.</span></span>

<span data-ttu-id="82e73-127">すべての複合現実アプリ用のコア ビルディング ブロックは、その他の Unity Api を使用した一貫性のある方法で公開されます。</span><span class="sxs-lookup"><span data-stu-id="82e73-127">All of the core building blocks for mixed reality apps are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="82e73-128">Mixed Reality Toolkit を使用します。</span><span class="sxs-lookup"><span data-stu-id="82e73-128">They are also available through Mixed Reality Toolkit.</span></span>
* [<span data-ttu-id="82e73-129">カメラ</span><span class="sxs-lookup"><span data-stu-id="82e73-129">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="82e73-130">座標系</span><span class="sxs-lookup"><span data-stu-id="82e73-130">Coordinate systems</span></span>](coordinate-systems-in-unity.md)
* [<span data-ttu-id="82e73-131">視線入力</span><span class="sxs-lookup"><span data-stu-id="82e73-131">Gaze</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="82e73-132">ジェスチャとアニメーション コント ローラー</span><span class="sxs-lookup"><span data-stu-id="82e73-132">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="82e73-133">音声入力</span><span class="sxs-lookup"><span data-stu-id="82e73-133">Voice input</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="82e73-134">永続化</span><span class="sxs-lookup"><span data-stu-id="82e73-134">Persistence</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="82e73-135">立体音響</span><span class="sxs-lookup"><span data-stu-id="82e73-135">Spatial sound</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="82e73-136">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="82e73-136">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="82e73-137">多くの複合現実アプリは、使用する Unity アプリにも公開するその他の主な機能があります。</span><span class="sxs-lookup"><span data-stu-id="82e73-137">There are other key features that many mixed reality apps will want to use, which are also exposed to Unity apps:</span></span>
* [<span data-ttu-id="82e73-138">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="82e73-138">Shared experiences</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="82e73-139">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="82e73-139">Locatable camera</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="82e73-140">フォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="82e73-140">Focus point</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="82e73-141">損失の追跡</span><span class="sxs-lookup"><span data-stu-id="82e73-141">Tracking loss</span></span>](tracking-loss-in-unity.md)
* <span data-ttu-id="82e73-142">[[キーボード]](keyboard-input-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="82e73-142">[Keyboard](keyboard-input-in-unity.md)</span></span>

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a><span data-ttu-id="82e73-143">実際、またはシミュレートされたデバイスで Unity プロジェクトを実行しています。</span><span class="sxs-lookup"><span data-stu-id="82e73-143">Running your Unity project on a real or simulated device</span></span>

<span data-ttu-id="82e73-144">次の手順は、ようになったら、holographic の Unity プロジェクトをテストする準備ができて、[をエクスポートし、Unity Visual Studio ソリューションをビルド](exporting-and-building-a-unity-visual-studio-solution.md)します。</span><span class="sxs-lookup"><span data-stu-id="82e73-144">Once you've got your holographic Unity project ready to test out, your next step is to [export and build a Unity Visual Studio solution](exporting-and-building-a-unity-visual-studio-solution.md).</span></span>

<span data-ttu-id="82e73-145">手の形でその VS ソリューションとできますし、アプリを実行する 3 つの方法のいずれかでいずれかを使用して実際またはシミュレーション上のデバイス。</span><span class="sxs-lookup"><span data-stu-id="82e73-145">With that VS solution in hand, you can then run your app in one of three ways, using either a real or simulated device:</span></span>
* [<span data-ttu-id="82e73-146">実際 HoloLens や Windows Mixed Reality イマーシブ ヘッドセットを展開します。</span><span class="sxs-lookup"><span data-stu-id="82e73-146">Deploy to a real HoloLens or Windows Mixed Reality immersive headset</span></span>](using-visual-studio.md)
* [<span data-ttu-id="82e73-147">HoloLens のエミュレーターへのデプロイします。</span><span class="sxs-lookup"><span data-stu-id="82e73-147">Deploy to the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="82e73-148">Windows Mixed Reality イマーシブ ヘッドセット シミュレーターへのデプロイします。</span><span class="sxs-lookup"><span data-stu-id="82e73-148">Deploy to the Windows Mixed Reality immersive headset simulator</span></span>](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a><span data-ttu-id="82e73-149">Unity のドキュメント</span><span class="sxs-lookup"><span data-stu-id="82e73-149">Unity documentation</span></span>

<span data-ttu-id="82e73-150">このドキュメントの他使用可能な Windows デベロッパー センターでは、Unity は Unity エディターと共に Windows Mixed Reality 機能のドキュメントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="82e73-150">In addition to this documentation available on the Windows Dev Center, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="82e73-151">Unity のドキュメントには、2 つのセクションが含まれています。 提供されています。</span><span class="sxs-lookup"><span data-stu-id="82e73-151">The Unity provided documentation includes two separate sections:</span></span>
1. <span data-ttu-id="82e73-152">**Unity スクリプトのリファレンス**</span><span class="sxs-lookup"><span data-stu-id="82e73-152">**Unity scripting reference**</span></span>
    * <span data-ttu-id="82e73-153">ドキュメントのこのセクションには、Unity が提供するスクリプト API の詳細が含まれています。</span><span class="sxs-lookup"><span data-stu-id="82e73-153">This section of the documentation contains details of the scripting API that Unity provides.</span></span>
    * <span data-ttu-id="82e73-154">Unity エディターからを通じてアクセス可能な**ヘルプ > スクリプトのリファレンス**</span><span class="sxs-lookup"><span data-stu-id="82e73-154">Accessible from the Unity Editor through **Help > Scripting Reference**</span></span>
2. <span data-ttu-id="82e73-155">**Unity マニュアル**</span><span class="sxs-lookup"><span data-stu-id="82e73-155">**Unity manual**</span></span>
    * <span data-ttu-id="82e73-156">このマニュアルは、高度な基本的な手法から Unity を使用する方法を学習するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="82e73-156">This manual is designed to help you learn how to use Unity, from basic to advanced techniques.</span></span>
    * <span data-ttu-id="82e73-157">Unity エディターからを通じてアクセス可能な**ヘルプ > 手動**</span><span class="sxs-lookup"><span data-stu-id="82e73-157">Accessible from the Unity Editor through **Help > Manual**</span></span>

## <a name="see-also"></a><span data-ttu-id="82e73-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="82e73-158">See also</span></span>
* [<span data-ttu-id="82e73-159">複合現実 Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="82e73-159">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="82e73-160">MR の基本 100:Unity の概要</span><span class="sxs-lookup"><span data-stu-id="82e73-160">MR Basics 100: Getting started with Unity</span></span>](holograms-100.md)
* [<span data-ttu-id="82e73-161">Unity で推奨される設定</span><span class="sxs-lookup"><span data-stu-id="82e73-161">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="82e73-162">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="82e73-162">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="82e73-163">Unity Visual Studio ソリューションのエクスポートとビルド</span><span class="sxs-lookup"><span data-stu-id="82e73-163">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="82e73-164">Windows 名前空間と HoloLens 用 Unity アプリの使用</span><span class="sxs-lookup"><span data-stu-id="82e73-164">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="82e73-165">Unity と Visual Studio を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="82e73-165">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="82e73-166">Unity の再生モード</span><span class="sxs-lookup"><span data-stu-id="82e73-166">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="82e73-167">移植のガイド</span><span class="sxs-lookup"><span data-stu-id="82e73-167">Porting guides</span></span>](porting-guides.md)
