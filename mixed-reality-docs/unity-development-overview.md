---
title: Unity 開発の概要
description: 構築の作業開始の複合現実アプリ Unity でします。
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity では、実際には、開発、作業の開始、新しいプロジェクト、移植、機能、カメラ、シミュレーション、エミュレーション、ドキュメントの混在
ms.openlocfilehash: 24217b4c61bf2d438ebc1c4114bc9dc20dc62f64
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414521"
---
# <a name="unity-development-overview"></a><span data-ttu-id="80a8c-104">Unity 開発の概要</span><span class="sxs-lookup"><span data-stu-id="80a8c-104">Unity development overview</span></span>

<span data-ttu-id="80a8c-105">最も高速パスのビルド方法、 [mixed reality アプリ](app-views.md)は[Unity](http://aka.ms/HoloLensUnity)。</span><span class="sxs-lookup"><span data-stu-id="80a8c-105">The fastest path to building a [mixed reality app](app-views.md) is with [Unity](http://aka.ms/HoloLensUnity).</span></span> <span data-ttu-id="80a8c-106">調査に時間がかかることをお勧め、 [Unity チュートリアル](https://unity3d.com/learn/tutorials)します。</span><span class="sxs-lookup"><span data-stu-id="80a8c-106">We recommend that you take time to explore the [Unity tutorials](https://unity3d.com/learn/tutorials).</span></span> <span data-ttu-id="80a8c-107">Unity が包括的で資産が必要な場合[Asset Store](https://www.assetstore.unity3d.com/)します。</span><span class="sxs-lookup"><span data-stu-id="80a8c-107">If you need assets, Unity has a comprehensive [Asset Store](https://www.assetstore.unity3d.com/).</span></span> <span data-ttu-id="80a8c-108">アクセスすることができます、Unity の基本的な知識を蓄積した後、[チュートリアル](tutorials.md)を Unity での複合現実開発の詳細を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80a8c-108">Once you have built up a basic understanding of Unity, you can visit the [tutorials](tutorials.md) to learn the specifics of mixed reality development with Unity.</span></span> <span data-ttu-id="80a8c-109">参照してください、 [Unity Mixed Reality フォーラム](http://forum.unity3d.com/forums/hololens.102/)が発生する問題の解決策を見つけて、コミュニティの構築、Unity での複合現実アプリの残りの部分とかかわります。</span><span class="sxs-lookup"><span data-stu-id="80a8c-109">Be sure to visit the [Unity Mixed Reality forums](http://forum.unity3d.com/forums/hololens.102/) to engage with the rest of the community building mixed reality apps in Unity and find solutions to problems you might run into.</span></span>


<span data-ttu-id="80a8c-110">まず、Unity を使用した複合現実アプリの構築を開始する[ツールをインストールする](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="80a8c-110">To get started building mixed reality apps with Unity, first [install the tools](install-the-tools.md).</span></span> 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a><span data-ttu-id="80a8c-111">Mixed Reality ツールキットを使用して新しい Unity プロジェクト</span><span class="sxs-lookup"><span data-stu-id="80a8c-111">New Unity Project with Mixed Reality Toolkit</span></span> 

<span data-ttu-id="80a8c-112">Unity での開発に最も簡単な方法は、Mixed Reality ツールキットのヘルプです。</span><span class="sxs-lookup"><span data-stu-id="80a8c-112">The easiest way to develop in Unity is with the help of Mixed Reality Toolkit.</span></span> <span data-ttu-id="80a8c-113">プロジェクトのセットアップのヘルプを自動的に、一連の開発を促進する複合現実の機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="80a8c-113">It will help you setup with project automatically, and provide a set of mixed reality features to accelerate your development.</span></span> <span data-ttu-id="80a8c-114">チェック アウトしてください[Mixed Reality Toolkit v2](mrtk-getting-started.md)詳細と開始します。</span><span class="sxs-lookup"><span data-stu-id="80a8c-114">Please check out [Mixed Reality Toolkit v2](mrtk-getting-started.md) to learn more and get started.</span></span> 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a><span data-ttu-id="80a8c-115">Windows Mixed Reality への既存の Unity アプリの移植</span><span class="sxs-lookup"><span data-stu-id="80a8c-115">Porting an existing Unity app to Windows Mixed Reality</span></span>

<span data-ttu-id="80a8c-116">Windows Mixed Reality を移植する既存の Unity プロジェクトを使用する場合はと共にに従って、 [Unity 移植のガイド](porting-guides.md)を開始します。</span><span class="sxs-lookup"><span data-stu-id="80a8c-116">If you have an existing Unity project that you're porting to Windows Mixed Reality, follow along with the [Unity porting guide](porting-guides.md) to get started.</span></span>

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="80a8c-117">新しい Unity プロジェクトを Windows Mixed Reality の構成</span><span class="sxs-lookup"><span data-stu-id="80a8c-117">Configuring new Unity project for Windows Mixed Reality</span></span>

<span data-ttu-id="80a8c-118">Mixed Reality ツールキットをインポートせず、新しい Unity プロジェクトを作成したい場合は、少数の Unity の設定が Windows Mixed Reality を手動で変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80a8c-118">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality.</span></span> <span data-ttu-id="80a8c-119">2 つのカテゴリに分かれています。 プロジェクトごとおよびシーンごと。</span><span class="sxs-lookup"><span data-stu-id="80a8c-119">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="80a8c-120">ステップ バイ ステップ ガイドについてはこちらを参照してください[新しい Unity プロジェクトの Windows Mixed Reality を構成する。](Configure-Unity-Project.md)</span><span class="sxs-lookup"><span data-stu-id="80a8c-120">See here for step by step guide to [Configure new Unity Project for Windows Mixed Reality](Configure-Unity-Project.md)</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="80a8c-121">複合現実の機能および入力の追加</span><span class="sxs-lookup"><span data-stu-id="80a8c-121">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="80a8c-122">プロジェクトとセットアップ MRTK V2 をしたか、前述のように、プロジェクトを構成すると、(カメラ) などの標準の Unity ゲーム オブジェクトが点灯直後の**取り付けられているスケール エクスペリエンス**カメラの位置を更新自動的にユーザーとして、世界中から自分の頭に移動します。</span><span class="sxs-lookup"><span data-stu-id="80a8c-122">Once you've setup MRTK V2 with your project, or configured your project as described above, standard Unity game objects (such as the camera) will light up immediately for a **seated-scale experience**, with the camera's position updated automatically as the user moves their head through the world.</span></span>

<span data-ttu-id="80a8c-123">Windows Mixed Reality の機能のサポートを追加するなど、[空間ステージ](coordinate-systems.md#spatial-coordinate-systems)、[ジェスチャ、モーションのコント ローラー](gestures-and-motion-controllers-in-unity.md)または[音声入力](voice-input-in-unity.md)に直接組み込まれている Api を使用して実現されますUnity です。</span><span class="sxs-lookup"><span data-stu-id="80a8c-123">Adding support for Windows Mixed Reality features, such as [spatial stages](coordinate-systems.md#spatial-coordinate-systems), [gestures, motion controllers](gestures-and-motion-controllers-in-unity.md) or [voice input](voice-input-in-unity.md) is achieved using APIs built directly into Unity.</span></span> 

<span data-ttu-id="80a8c-124">最初に、確認、[スケールが発生する](coordinate-systems.md)applicatioin を対象とします。</span><span class="sxs-lookup"><span data-stu-id="80a8c-124">First, review the [experience scales](coordinate-systems.md) that your applicatioin can target:</span></span>
* <span data-ttu-id="80a8c-125">ビルドに必要な場合、**向き専用**または**取り付けられているスケール エクスペリエンス**、設定する必要があります Unity に領域の種類の追跡の[静止](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="80a8c-125">If you're looking to build an **orientation-only** or **seated-scale experience**, you'll need to set Unity's tracking space type to [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="80a8c-126">ビルドに必要な場合、**継続スケール**または**ルーム スケール エクスペリエンス**、Unity のことを確認する必要がありますに正常に設定されて領域の種類を追跡[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)します。</span><span class="sxs-lookup"><span data-stu-id="80a8c-126">If you're looking to build a **standing-scale** or **room-scale experience**, you'll need to ensure Unity's tracking space type is successfully set to [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="80a8c-127">ビルドに必要な場合、**世界規模**エクスペリエンスでユーザーが 5 m を超えるローミングできる HoloLens、使用する必要があります、 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="80a8c-127">If you're looking to build a **world-scale** experience on HoloLens that lets users roam beyond 5 meters, you'll need to use the [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) component.</span></span>

<span data-ttu-id="80a8c-128">すべての複合現実のアプリケーション用のコア ビルディング ブロックは、その他の Unity Api を使用した一貫性のある方法で公開されます。</span><span class="sxs-lookup"><span data-stu-id="80a8c-128">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="80a8c-129">Mixed Reality Toolkit を使用します。</span><span class="sxs-lookup"><span data-stu-id="80a8c-129">They are also available through the Mixed Reality Toolkit.</span></span>
* [<span data-ttu-id="80a8c-130">カメラ</span><span class="sxs-lookup"><span data-stu-id="80a8c-130">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="80a8c-131">座標系</span><span class="sxs-lookup"><span data-stu-id="80a8c-131">Coordinate systems</span></span>](coordinate-systems-in-unity.md)
* [<span data-ttu-id="80a8c-132">視線入力</span><span class="sxs-lookup"><span data-stu-id="80a8c-132">Gaze</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="80a8c-133">ジェスチャとアニメーション コント ローラー</span><span class="sxs-lookup"><span data-stu-id="80a8c-133">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="80a8c-134">音声入力</span><span class="sxs-lookup"><span data-stu-id="80a8c-134">Voice input</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="80a8c-135">永続化</span><span class="sxs-lookup"><span data-stu-id="80a8c-135">Persistence</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="80a8c-136">立体音響</span><span class="sxs-lookup"><span data-stu-id="80a8c-136">Spatial sound</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="80a8c-137">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="80a8c-137">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="80a8c-138">その他のキーの機能が多く、複合現実には、アプリケーションを使用する Unity アプリにも公開されています。</span><span class="sxs-lookup"><span data-stu-id="80a8c-138">There are other key features that many mixed reality applications will want to use that are also exposed to Unity apps:</span></span>
* [<span data-ttu-id="80a8c-139">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="80a8c-139">Shared experiences</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="80a8c-140">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="80a8c-140">Locatable camera</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="80a8c-141">フォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="80a8c-141">Focus point</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="80a8c-142">損失の追跡</span><span class="sxs-lookup"><span data-stu-id="80a8c-142">Tracking loss</span></span>](tracking-loss-in-unity.md)
* <span data-ttu-id="80a8c-143">[[キーボード]](keyboard-input-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="80a8c-143">[Keyboard](keyboard-input-in-unity.md)</span></span>

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a><span data-ttu-id="80a8c-144">実際、またはシミュレートされたデバイスで Unity プロジェクトを実行しています。</span><span class="sxs-lookup"><span data-stu-id="80a8c-144">Running your Unity project on a real or simulated device</span></span>

<span data-ttu-id="80a8c-145">次の手順はようになったら、holographic の Unity プロジェクトをテストするための準備ができて、[をエクスポートし、Unity Visual Studio ソリューションをビルド](exporting-and-building-a-unity-visual-studio-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="80a8c-145">Once you've got your holographic Unity project ready for testing, your next step is to [export and build a Unity Visual Studio solution](exporting-and-building-a-unity-visual-studio-solution.md).</span></span>

<span data-ttu-id="80a8c-146">手の形でその VS ソリューションとできますし、アプリケーションを実行する 3 つの方法のいずれかでいずれかを使用して実際またはシミュレーション上のデバイス。</span><span class="sxs-lookup"><span data-stu-id="80a8c-146">With that VS solution in hand, you can then run your application in one of three ways, using either a real or simulated device:</span></span>
* [<span data-ttu-id="80a8c-147">実際 HoloLens や Windows Mixed Reality イマーシブ ヘッドセットを展開します。</span><span class="sxs-lookup"><span data-stu-id="80a8c-147">Deploy to a real HoloLens or Windows Mixed Reality immersive headset</span></span>](using-visual-studio.md)
* [<span data-ttu-id="80a8c-148">HoloLens のエミュレーターへのデプロイします。</span><span class="sxs-lookup"><span data-stu-id="80a8c-148">Deploy to the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="80a8c-149">Windows Mixed Reality イマーシブ ヘッドセット シミュレーターへのデプロイします。</span><span class="sxs-lookup"><span data-stu-id="80a8c-149">Deploy to the Windows Mixed Reality immersive headset simulator</span></span>](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a><span data-ttu-id="80a8c-150">Unity のドキュメント</span><span class="sxs-lookup"><span data-stu-id="80a8c-150">Unity documentation</span></span>

<span data-ttu-id="80a8c-151">このドキュメントの他使用可能な Windows デベロッパー センターでは、Unity は Unity エディターと共に Windows Mixed Reality 機能のドキュメントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="80a8c-151">In addition to this documentation available on the Windows Dev Center, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="80a8c-152">Unity のドキュメントには、2 つのセクションが含まれています。 提供されています。</span><span class="sxs-lookup"><span data-stu-id="80a8c-152">The Unity provided documentation includes two separate sections:</span></span>
1. <span data-ttu-id="80a8c-153">**Unity スクリプトのリファレンス**</span><span class="sxs-lookup"><span data-stu-id="80a8c-153">**Unity scripting reference**</span></span>
    * <span data-ttu-id="80a8c-154">ドキュメントのこのセクションには、Unity が提供するスクリプト API の詳細が含まれています。</span><span class="sxs-lookup"><span data-stu-id="80a8c-154">This section of the documentation contains details of the scripting API that Unity provides.</span></span>
    * <span data-ttu-id="80a8c-155">Unity エディターからを通じてアクセス可能な**ヘルプ > スクリプトのリファレンス**</span><span class="sxs-lookup"><span data-stu-id="80a8c-155">Accessible from the Unity Editor through **Help > Scripting Reference**</span></span>
2. <span data-ttu-id="80a8c-156">**Unity マニュアル**</span><span class="sxs-lookup"><span data-stu-id="80a8c-156">**Unity manual**</span></span>
    * <span data-ttu-id="80a8c-157">このマニュアルは、高度な基本的な手法から Unity を使用する方法を学習するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="80a8c-157">This manual is designed to help you learn how to use Unity, from basic to advanced techniques.</span></span>
    * <span data-ttu-id="80a8c-158">Unity エディターからを通じてアクセス可能な**ヘルプ > 手動**</span><span class="sxs-lookup"><span data-stu-id="80a8c-158">Accessible from the Unity Editor through **Help > Manual**</span></span>

## <a name="see-also"></a><span data-ttu-id="80a8c-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="80a8c-159">See also</span></span>
* [<span data-ttu-id="80a8c-160">複合現実 Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="80a8c-160">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="80a8c-161">MR の基本 100:Unity の概要</span><span class="sxs-lookup"><span data-stu-id="80a8c-161">MR Basics 100: Getting started with Unity</span></span>](holograms-100.md)
* [<span data-ttu-id="80a8c-162">Unity で推奨される設定</span><span class="sxs-lookup"><span data-stu-id="80a8c-162">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="80a8c-163">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="80a8c-163">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="80a8c-164">Unity Visual Studio ソリューションのエクスポートとビルド</span><span class="sxs-lookup"><span data-stu-id="80a8c-164">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="80a8c-165">Windows 名前空間と HoloLens 用 Unity アプリの使用</span><span class="sxs-lookup"><span data-stu-id="80a8c-165">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="80a8c-166">Unity と Visual Studio を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="80a8c-166">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="80a8c-167">Unity の再生モード</span><span class="sxs-lookup"><span data-stu-id="80a8c-167">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="80a8c-168">移植のガイド</span><span class="sxs-lookup"><span data-stu-id="80a8c-168">Porting guides</span></span>](porting-guides.md)
