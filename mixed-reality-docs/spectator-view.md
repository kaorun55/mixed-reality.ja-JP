---
title: Spectator ビュー
description: 外付けディスプレイでの複合現実エクスペリエンスのデモまたは複合現実エクスペリエンスのビデオを記録するための手段として、外部デバイスからホログラムを視覚化します。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator ビュー、iPhone、iOS、iPad、OpenCV、カメラ、ARKit、HoloLens、Mixed Reality、MixedRealityToolkit、デモでは、レコード
ms.openlocfilehash: 77102cf5fb1c23f27f7f2d651c6ca1ae9df5a1d1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602271"
---
# <a name="spectator-view-for-hololens"></a><span data-ttu-id="48af3-104">HoloLens の spectator ビュー</span><span class="sxs-lookup"><span data-stu-id="48af3-104">Spectator View for HoloLens</span></span>

![Marker](images/SpecViewPhoneHero.jpg)


## <a name="current-refactor"></a><span data-ttu-id="48af3-106">現在のリファクタリング</span><span class="sxs-lookup"><span data-stu-id="48af3-106">Current Refactor</span></span>

> [!NOTE]
><span data-ttu-id="48af3-107">HoloLens の spectator ビューのリファクタリングがアクティブにされています。</span><span class="sxs-lookup"><span data-stu-id="48af3-107">Spectator View for HoloLens is being actively refactored.</span></span> <span data-ttu-id="48af3-108">この作業は、プレビューを統合するためのものが、それをコードベースし、Pro HoloLens 2 のサポートを拡張します。</span><span class="sxs-lookup"><span data-stu-id="48af3-108">This work is intended to consolidate the Preview and Pro codebases and extend support to HoloLens 2.</span></span> 

<span data-ttu-id="48af3-109">現在の表示 Spectator ビューのリファクタリングの状態は MixedRealityToolkit と MixedRealityToolkit Unity の両方のリポジトリにある '機能/spectatorView' ブランチを参照してください。</span><span class="sxs-lookup"><span data-stu-id="48af3-109">To view the current state of the Spectator View refactor see 'feature/spectatorView' branches in both the MixedRealityToolkit and MixedRealityToolkit-Unity repos:</span></span>

https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/feature/spectatorView/Assets/MixedRealityToolkit.Extensions/SpectatorView

<span data-ttu-id="48af3-110">、</span><span class="sxs-lookup"><span data-stu-id="48af3-110">and</span></span>

https://github.com/Microsoft/MixedRealityToolkit/tree/feature/spectatorView/SpectatorViewPlugin

## <a name="overview"></a><span data-ttu-id="48af3-111">概要</span><span class="sxs-lookup"><span data-stu-id="48af3-111">Overview</span></span>

<span data-ttu-id="48af3-112">ソックスを着けずに、HoloLens、ときに多くの場合、忘れている人を持たないことはできる信じられないことが発生することができません。</span><span class="sxs-lookup"><span data-stu-id="48af3-112">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="48af3-113">Spectator ビューを使用して、HoloLens ユーザーが自分の世界では 2D 画面に表示する使用できます。</span><span class="sxs-lookup"><span data-stu-id="48af3-113">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="48af3-114">Spectator ビュー (プレビュー) は、Spectator ビュー Pro ホログラムのプロ品質の記録の目的は、HD でホログラムの記録に高速で低コストのアプローチです。</span><span class="sxs-lookup"><span data-stu-id="48af3-114">Spectator View (Preview) is fast and affordable approach to recording holograms in HD, while Spectator View Pro is intended for professional quality recording of holograms.</span></span>

<span data-ttu-id="48af3-115">次の表は、両方のオプションとその機能を示します。</span><span class="sxs-lookup"><span data-stu-id="48af3-115">The following table shows both options and their capabilities.</span></span> <span data-ttu-id="48af3-116">ビデオ記録のニーズに最適なオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="48af3-116">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="48af3-117">Spectator ビュー (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="48af3-117">Spectator View (Preview)</span></span> |              <span data-ttu-id="48af3-118">Spectator Pro の表示</span><span class="sxs-lookup"><span data-stu-id="48af3-118">Spectator View Pro</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="48af3-119">HD 品質</span><span class="sxs-lookup"><span data-stu-id="48af3-119">HD quality</span></span>                         |         <span data-ttu-id="48af3-120">フル HD</span><span class="sxs-lookup"><span data-stu-id="48af3-120">Full HD</span></span>         |        <span data-ttu-id="48af3-121">映画 (DSLR によって決定されます)、プロの品質</span><span class="sxs-lookup"><span data-stu-id="48af3-121">Professional quality filming (as determined by DSLR)</span></span>      |
| <span data-ttu-id="48af3-122">簡単なカメラの動き</span><span class="sxs-lookup"><span data-stu-id="48af3-122">Easy camera movement</span></span>                      |            <span data-ttu-id="48af3-123">✔</span><span class="sxs-lookup"><span data-stu-id="48af3-123">✔</span></span>            |                                             |
| <span data-ttu-id="48af3-124">3 人目のビュー</span><span class="sxs-lookup"><span data-stu-id="48af3-124">Third-person view</span></span>                    |            <span data-ttu-id="48af3-125">✔</span><span class="sxs-lookup"><span data-stu-id="48af3-125">✔</span></span>            |                      <span data-ttu-id="48af3-126">✔</span><span class="sxs-lookup"><span data-stu-id="48af3-126">✔</span></span>                      |
| <span data-ttu-id="48af3-127">画面にストリームすることができます。</span><span class="sxs-lookup"><span data-stu-id="48af3-127">Can be streamed to screens</span></span>           |            <span data-ttu-id="48af3-128">✔</span><span class="sxs-lookup"><span data-stu-id="48af3-128">✔</span></span>            |                      <span data-ttu-id="48af3-129">✔</span><span class="sxs-lookup"><span data-stu-id="48af3-129">✔</span></span>                      |
| <span data-ttu-id="48af3-130">移植性があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-130">Portable</span></span>                             |            <span data-ttu-id="48af3-131">✔</span><span class="sxs-lookup"><span data-stu-id="48af3-131">✔</span></span>            |                                             |
| <span data-ttu-id="48af3-132">ワイヤレス</span><span class="sxs-lookup"><span data-stu-id="48af3-132">Wireless</span></span>                             |            <span data-ttu-id="48af3-133">✔</span><span class="sxs-lookup"><span data-stu-id="48af3-133">✔</span></span>            |                                             |
| <span data-ttu-id="48af3-134">必要なハードウェアの追加</span><span class="sxs-lookup"><span data-stu-id="48af3-134">Additional required hardware</span></span>         |     <span data-ttu-id="48af3-135">(iPhone または iPad)</span><span class="sxs-lookup"><span data-stu-id="48af3-135">iPhone (or iPad)</span></span>    | <span data-ttu-id="48af3-136">HoloLens + リモート テスト マシン群 + 三脚 + DSLR + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="48af3-136">HoloLens + Rig + Tripod + DSLR + PC + Unity</span></span> |
| <span data-ttu-id="48af3-137">ハードウェアへの投資</span><span class="sxs-lookup"><span data-stu-id="48af3-137">Hardware investment</span></span>                  |           <span data-ttu-id="48af3-138">低</span><span class="sxs-lookup"><span data-stu-id="48af3-138">Low</span></span>           |                     <span data-ttu-id="48af3-139">高</span><span class="sxs-lookup"><span data-stu-id="48af3-139">High</span></span>                    |
| <span data-ttu-id="48af3-140">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="48af3-140">Cross-platform</span></span>                       |           <span data-ttu-id="48af3-141">iOS</span><span class="sxs-lookup"><span data-stu-id="48af3-141">iOS</span></span>           |                                             |
| <span data-ttu-id="48af3-142">ビューアーが対話することができます。</span><span class="sxs-lookup"><span data-stu-id="48af3-142">Viewer can interact</span></span>                  |            <span data-ttu-id="48af3-143">✔</span><span class="sxs-lookup"><span data-stu-id="48af3-143">✔</span></span>            |                                             |
| <span data-ttu-id="48af3-144">ネットワークも不要です (UNET スクリプト)</span><span class="sxs-lookup"><span data-stu-id="48af3-144">Networking required (UNET scripting)</span></span> |            <span data-ttu-id="48af3-145">✔</span><span class="sxs-lookup"><span data-stu-id="48af3-145">✔</span></span>            |                      <span data-ttu-id="48af3-146">✔</span><span class="sxs-lookup"><span data-stu-id="48af3-146">✔</span></span>                      |
| <span data-ttu-id="48af3-147">ランタイムのセットアップの実行時間</span><span class="sxs-lookup"><span data-stu-id="48af3-147">Runtime setup duration</span></span>               |         <span data-ttu-id="48af3-148">インスタント</span><span class="sxs-lookup"><span data-stu-id="48af3-148">Instant</span></span>         |                     <span data-ttu-id="48af3-149">スロー (低速)</span><span class="sxs-lookup"><span data-stu-id="48af3-149">Slow</span></span>                    |

## <a name="spectator-view-preview"></a><span data-ttu-id="48af3-150">Spectator ビュー (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="48af3-150">Spectator View (Preview)</span></span>

![Marker](images/SpecViewPhoneDemo.jpg)

### <a name="use-cases"></a><span data-ttu-id="48af3-152">使用事例</span><span class="sxs-lookup"><span data-stu-id="48af3-152">Use cases</span></span>

- <span data-ttu-id="48af3-153">HD の映画ホログラム:Spectator ビュー (プレビュー) を使用して、iPhone を使用して、複合現実エクスペリエンスを記録できます。</span><span class="sxs-lookup"><span data-stu-id="48af3-153">Filming holograms in HD: Using Spectator View (Preview), you can record a mixed reality experience using an iPhone.</span></span> <span data-ttu-id="48af3-154">フル HD に記録し、ホログラムともシャドウにアンチエイリアシングを適用します。</span><span class="sxs-lookup"><span data-stu-id="48af3-154">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="48af3-155">ホログラムのビデオをキャプチャするコスト効率に優れた、簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="48af3-155">It is a cost-effective and quick way to capture video of holograms.</span></span>
- <span data-ttu-id="48af3-156">ライブ デモ:IPhone または iPad では、lag フリーから直接、Apple TV エクスペリエンス Stream ライブ複合現実です。</span><span class="sxs-lookup"><span data-stu-id="48af3-156">Live demos: Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
- <span data-ttu-id="48af3-157">ゲストのエクスペリエンスを共有します。HoloLens 以外のユーザーのスマート フォンまたはタブレットから直接ホログラムが発生することができるようにします。</span><span class="sxs-lookup"><span data-stu-id="48af3-157">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

### <a name="current-features"></a><span data-ttu-id="48af3-158">現在の機能</span><span class="sxs-lookup"><span data-stu-id="48af3-158">Current features</span></span>

- <span data-ttu-id="48af3-159">スマート フォンをセッションに追加するための自動検出をネットワークです。</span><span class="sxs-lookup"><span data-stu-id="48af3-159">Network auto-discovery for adding phones to the session.</span></span>
- <span data-ttu-id="48af3-160">セッションの自動処理をため、ユーザーが正しいセッションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="48af3-160">Automatic session handling, so users are added to the correct session.</span></span>
- <span data-ttu-id="48af3-161">ホログラム、ホログラム正確な同じ場所に表示されるすべてのユーザーのための空間同期します。</span><span class="sxs-lookup"><span data-stu-id="48af3-161">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
- <span data-ttu-id="48af3-162">iOS では、(ARKit が有効なデバイス) をサポートします。</span><span class="sxs-lookup"><span data-stu-id="48af3-162">iOS support (ARKit-enabled devices).</span></span>
- <span data-ttu-id="48af3-163">IOS の複数のゲストです。</span><span class="sxs-lookup"><span data-stu-id="48af3-163">Multiple iOS guests.</span></span>
- <span data-ttu-id="48af3-164">ビデオ + ホログラム + 環境音ホログラム サウンドの録音。</span><span class="sxs-lookup"><span data-stu-id="48af3-164">Recording of video + holograms + ambient sound + hologram sound.</span></span>
- <span data-ttu-id="48af3-165">ビデオを保存、電子メール、またはその他のサポートのアプリと共有するために、シートを共有します。</span><span class="sxs-lookup"><span data-stu-id="48af3-165">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>


>[!NOTE] 
><span data-ttu-id="48af3-166">Spectator ビュー (プレビュー) のコードは、Spectator ビュー Pro バージョンのコードでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="48af3-166">The Spectator View (Preview) code cannot be used with the Spectator View Pro version code.</span></span> <span data-ttu-id="48af3-167">ホログラムのビデオ記録が必要な場合、新しいプロジェクトでの実装をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="48af3-167">We recommend to implement it in new projects where video recording of holograms is required.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/3fXlPw_FGLg]


### <a name="licenses"></a><span data-ttu-id="48af3-168">ライセンス</span><span class="sxs-lookup"><span data-stu-id="48af3-168">Licenses</span></span>

- [<span data-ttu-id="48af3-169">OpenCV - (3 句 BSD ライセンス)</span><span class="sxs-lookup"><span data-stu-id="48af3-169">OpenCV - (3-clause BSD License)</span></span>](https://opencv.org/license.html)
- [<span data-ttu-id="48af3-170">Unity ARKit - (MIT ライセンス)</span><span class="sxs-lookup"><span data-stu-id="48af3-170">Unity ARKit - (MIT License)</span></span>](https://bitbucket.org/Unity-Technologies/unity-arkit-plugin/src/3691df77caca2095d632c5e72ff4ffa68ced111f/LICENSES/MIT_LICENSE?at=default&fileviewer=file-view-default)

## <a name="how-to-set-up-spectator-view-preview"></a><span data-ttu-id="48af3-171">Spectator ビュー (プレビュー) を設定する方法</span><span class="sxs-lookup"><span data-stu-id="48af3-171">How to set up Spectator View (Preview)</span></span>

### <a name="requirements"></a><span data-ttu-id="48af3-172">要件</span><span class="sxs-lookup"><span data-stu-id="48af3-172">Requirements</span></span>

- <span data-ttu-id="48af3-173">[Spectator ビュー プラグインと必要な OpenCV バイナリ](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)-Spectator ビューのネイティブ プラグインを構築する方法の詳細については下にあります。</span><span class="sxs-lookup"><span data-stu-id="48af3-173">[Spectator View plugin and required OpenCV binaries](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin) - Details on how to build the Spectator View Native Plugin can be found below.</span></span> <span data-ttu-id="48af3-174">生成されたバイナリからは、次の必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-174">From the generated binaries you will need:</span></span>

    - <span data-ttu-id="48af3-175">opencv_aruco343.dll</span><span class="sxs-lookup"><span data-stu-id="48af3-175">opencv_aruco343.dll</span></span>
    - <span data-ttu-id="48af3-176">opencv_calib3d343.dll</span><span class="sxs-lookup"><span data-stu-id="48af3-176">opencv_calib3d343.dll</span></span>
    - <span data-ttu-id="48af3-177">opencv_core343.dll</span><span class="sxs-lookup"><span data-stu-id="48af3-177">opencv_core343.dll</span></span>
    - <span data-ttu-id="48af3-178">opencv_features2d343.dll</span><span class="sxs-lookup"><span data-stu-id="48af3-178">opencv_features2d343.dll</span></span>
    - <span data-ttu-id="48af3-179">opencv_flann343.dll</span><span class="sxs-lookup"><span data-stu-id="48af3-179">opencv_flann343.dll</span></span>
    - <span data-ttu-id="48af3-180">opencv_imgproc343.dll</span><span class="sxs-lookup"><span data-stu-id="48af3-180">opencv_imgproc343.dll</span></span>

    - <span data-ttu-id="48af3-181">zlib1.dll</span><span class="sxs-lookup"><span data-stu-id="48af3-181">zlib1.dll</span></span>
    - <span data-ttu-id="48af3-182">SpectatorViewPlugin.dll</span><span class="sxs-lookup"><span data-stu-id="48af3-182">SpectatorViewPlugin.dll</span></span>
- <span data-ttu-id="48af3-183">Spectator ビューでは、そのネットワークの検出と空間的な同期の Unity Networking (UNET) を使用します。</span><span class="sxs-lookup"><span data-stu-id="48af3-183">Spectator View uses Unity Networking (UNET) for its network discovery and spatial syncing.</span></span> <span data-ttu-id="48af3-184">つまり、アプリケーションの中にすべての対話機能をデバイス間で同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-184">This means all interactivity during the application needs to be synced between the devices.</span></span>
- <span data-ttu-id="48af3-185">Unity 2017.2.1p2 またはそれ以降</span><span class="sxs-lookup"><span data-stu-id="48af3-185">Unity 2017.2.1p2 or later</span></span>
- <span data-ttu-id="48af3-186">ハードウェア</span><span class="sxs-lookup"><span data-stu-id="48af3-186">Hardware</span></span>
    - <span data-ttu-id="48af3-187">HoloLens、</span><span class="sxs-lookup"><span data-stu-id="48af3-187">A HoloLens</span></span>
    - <span data-ttu-id="48af3-188">Windows 10 を実行している Windows PC</span><span class="sxs-lookup"><span data-stu-id="48af3-188">Windows PC running Windows 10</span></span>
    - <span data-ttu-id="48af3-189">ARKit 互換性のあるデバイス (iPhone 6 s 以降/iPad Pro 2016 以降/iPad 2017 以降)-iOS 11 を実行している以上</span><span class="sxs-lookup"><span data-stu-id="48af3-189">ARKit compatible device (iPhone 6s onwards / iPad Pro 2016 onwards / iPad 2017 onwards) - running iOS 11 or above</span></span>
    - <span data-ttu-id="48af3-190">Mac で xcode 9.2 以降</span><span class="sxs-lookup"><span data-stu-id="48af3-190">Mac with xcode 9.2 onwards</span></span>
- <span data-ttu-id="48af3-191">Apple 開発者アカウント、無料または[有料](https://developer.apple.com/)</span><span class="sxs-lookup"><span data-stu-id="48af3-191">Apple developer account, free or [paid](https://developer.apple.com/)</span></span>
- <span data-ttu-id="48af3-192">Microsoft Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="48af3-192">Microsoft Visual Studio 2017</span></span>

### <a name="building-the-spectator-view-native-plugin"></a><span data-ttu-id="48af3-193">Spectator ビューのネイティブ プラグインを構築</span><span class="sxs-lookup"><span data-stu-id="48af3-193">Building the Spectator View native plugin</span></span>

<span data-ttu-id="48af3-194">必要なファイルを生成するには、次の手順を実行します。 https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md</span><span class="sxs-lookup"><span data-stu-id="48af3-194">To generate the required files, follow these steps: https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md</span></span>

### <a name="project-setup"></a><span data-ttu-id="48af3-195">プロジェクトのセットアップ</span><span class="sxs-lookup"><span data-stu-id="48af3-195">Project setup</span></span>

1. <span data-ttu-id="48af3-196">シーン内のすべての見える gameobjects は、世界のルート gameobject の下に含まれていることを確認、シーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="48af3-196">Prepare your scene, ensuring all visable gameobjects within your scene are contained under a world root gameobject.</span></span>

    ![世界のルート](images/SpecViewPhoneWorldRoot2.PNG)

2. <span data-ttu-id="48af3-198">SpectatorView プレハブの追加 ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) シーンにします。</span><span class="sxs-lookup"><span data-stu-id="48af3-198">Add the SpectatorView prefab ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) into your scene.</span></span>
3. <span data-ttu-id="48af3-199">SpectatorViewNetworking プレハブの追加 ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) シーンにします。</span><span class="sxs-lookup"><span data-stu-id="48af3-199">Add the SpectatorViewNetworking prefab ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) into your scene.</span></span>
4. <span data-ttu-id="48af3-200">SpectatorViewNetworking gameobject を選択し、SpectatorViewNetworkingManager コンポーネントには、いくつかの点をリンクすることができます。</span><span class="sxs-lookup"><span data-stu-id="48af3-200">Select the SpectatorViewNetworking gameobject and on the SpectatorViewNetworkingManager component, there's a few things you can link up.</span></span> <span data-ttu-id="48af3-201">左はそのまま残る場合、このコンポーネントは、実行時に必要なスクリプトの検索されます。</span><span class="sxs-lookup"><span data-stu-id="48af3-201">If left untouched this component will search for necessary scripts at runtime.</span></span>
    - <span data-ttu-id="48af3-202">マーカー検出 HoloLens SpectatorView/Hololens/MarkerDetection を -> します。</span><span class="sxs-lookup"><span data-stu-id="48af3-202">Marker Detection HoloLens -> SpectatorView/Hololens/MarkerDetection</span></span>
    - <span data-ttu-id="48af3-203">マーカー生成 3D SpectatorView、IPhone、SyncMarker/3DMarker を -> します。</span><span class="sxs-lookup"><span data-stu-id="48af3-203">Marker Generation 3D -> SpectatorView/IPhone/SyncMarker/3DMarker</span></span>

    ![SpectatorView ネットワーク探索](images/SpecViewPhoneNetworkDiscovery.PNG)

### <a name="networking-your-app"></a><span data-ttu-id="48af3-205">アプリのネットワーク</span><span class="sxs-lookup"><span data-stu-id="48af3-205">Networking your app</span></span>

- <span data-ttu-id="48af3-206">Spectator 表示では、そのネットワークの UNET が使われのすべてのホスト クライアント接続を管理します。</span><span class="sxs-lookup"><span data-stu-id="48af3-206">Spectator View uses UNET for its networking and manages all host-client connections for you.</span></span>
- <span data-ttu-id="48af3-207">アプリの特定のデータは、同期され、SyncVars、NetworkTransform、NetworkBehavior などを使用して実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-207">Any app specific data has to be synced and implemented by you, using e.g. SyncVars, NetworkTransform, NetworkBehavior.</span></span>
- <span data-ttu-id="48af3-208">Unity のネットワークの詳細については次を参照してください[マルチ プレーヤーとネットワーク](https://docs.unity3d.com/Manual/UNet.html)します。</span><span class="sxs-lookup"><span data-stu-id="48af3-208">For more information on Unity Networking please visit [Multiplayer and Networking](https://docs.unity3d.com/Manual/UNet.html).</span></span> <span data-ttu-id="48af3-209">(注。UNet は非推奨とされました。Spectator ビュー コードベースの現在のリファクタリングは、この問題に対処されます)</span><span class="sxs-lookup"><span data-stu-id="48af3-209">(Note: UNet has been deprecated; the current refactor of the Spectator View codebase will address this issue)</span></span>

### <a name="building-for-each-platform-hololens-or-ios"></a><span data-ttu-id="48af3-210">HoloLens (iOS) は、各プラットフォームの構築</span><span class="sxs-lookup"><span data-stu-id="48af3-210">Building for each platform (HoloLens or iOS)</span></span>

- <span data-ttu-id="48af3-211">IOS をビルドする場合は、まだこのプラットフォームと互換性はないために、MRTK の GLTF コンポーネントを削除するを確認します。</span><span class="sxs-lookup"><span data-stu-id="48af3-211">When building for iOS, ensure you remove the GLTF component of MRTK as this is not yet compatible with this platform.</span></span>
- <span data-ttu-id="48af3-212">SpectatorView プレハブの最上位レベルでは、' プラットフォーム スイッチャー ' と呼ばれるコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="48af3-212">At the top level of the SpectatorView prefab there is a component called 'Platform Switcher'.</span></span> <span data-ttu-id="48af3-213">ビルドするプラットフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="48af3-213">Select the platform you want to build for.</span></span>
    - <span data-ttu-id="48af3-214">'Hololens' を選択した場合、非アクティブになる SpectatorView プレハブで iPhone gameobject の下にあるすべての gameobject とアクティブになる 'Hololens' 下のすべての gameobject が表示されます。</span><span class="sxs-lookup"><span data-stu-id="48af3-214">If selecting 'Hololens' you should see all gameobjects beneath the iPhone gameobject in the SpectatorView prefab become inactive and all the gameobjects under 'Hololens' become active.</span></span>
    - <span data-ttu-id="48af3-215">これは少し時間がかかるプラットフォームによって選択すると、HoloToolkit されているプロジェクトの追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="48af3-215">This can take a little while as depending on the platform you choose the HoloToolkit is being added or removed from the project.</span></span>

    ![プラットフォームのスイッチャー](images/SpecViewPhoneSwitcher.PNG)

- <span data-ttu-id="48af3-217">Unity と未解決の問題により同じ Unity エディターのインスタンス (do 間終了させない Unity のビルド) を使用してアプリケーションのすべてのバージョンをビルドすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="48af3-217">Ensure you build all versions of the application using the same Unity editor instance (do not close Unity between builds) due to an unresolved issue with Unity.</span></span>

### <a name="running-your-app"></a><span data-ttu-id="48af3-218">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="48af3-218">Running your app</span></span>

<span data-ttu-id="48af3-219">作成すると、デプロイするアプリケーションの iPhone と HoloLens のバージョンが、これらを接続することができる必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-219">Once you have built and deployed a version of you application on iPhone and on HoloLens, you should be able to connect them.</span></span>

1. <span data-ttu-id="48af3-220">デバイスの両方を同じ Wi-fi ネットワークにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="48af3-220">Ensure that both devices are on the same Wi-Fi network.</span></span>
2. <span data-ttu-id="48af3-221">不特定の順序で、両デバイスでアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="48af3-221">Start the application on the both devices, in no specific order.</span></span> <span data-ttu-id="48af3-222">Iphone の場合、アプリケーションを開始するプロセスは、HoloLens のカメラをオンにし、写真が撮影を開始をトリガーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-222">The process of starting the application on the iPhone should trigger the HoloLens camera to turn on and begin taking pictures.</span></span>
3. <span data-ttu-id="48af3-223">IPhone アプリが起動するとすぐに、床やテーブルなどのサーフェスを検索します。</span><span class="sxs-lookup"><span data-stu-id="48af3-223">As soon as iPhone app starts, it will look for surfaces like floors or tables.</span></span> <span data-ttu-id="48af3-224">サーフェスが見つかった場合は、次のようなマーカーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="48af3-224">When surfaces are found, you should see a marker similar to the one below.</span></span> <span data-ttu-id="48af3-225">HoloLens にこのマーカーを表示します。</span><span class="sxs-lookup"><span data-stu-id="48af3-225">Show this marker to the HoloLens.</span></span>

    ![Marker](images/SpecViewPhoneMarker.PNG)

4. <span data-ttu-id="48af3-227">マーカーが検出されましたが非表示、HoloLens とデバイスの両方の接続し空間的に同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-227">Once the marker has been detected by the HoloLens it should disappear and both devices should be connected and spatially synced.</span></span>

### <a name="recording-video"></a><span data-ttu-id="48af3-228">記録のビデオ</span><span class="sxs-lookup"><span data-stu-id="48af3-228">Recording video</span></span>

1. <span data-ttu-id="48af3-229">IPhone からビデオを保存して、キャプチャをタップし、1 秒間、画面を保持します。</span><span class="sxs-lookup"><span data-stu-id="48af3-229">To capture and save a video from the iPhone, tap and hold the screen for 1 second.</span></span> <span data-ttu-id="48af3-230">これにより、記録メニューが開きます。</span><span class="sxs-lookup"><span data-stu-id="48af3-230">This will open the recording menu.</span></span>
2. <span data-ttu-id="48af3-231">赤い録画ボタンをタップして、画面の記録を開始する前に、カウント ダウンが開始されます。</span><span class="sxs-lookup"><span data-stu-id="48af3-231">Tap the red record button, this will start a countdown before beginning to record the screen.</span></span>
3. <span data-ttu-id="48af3-232">記録タップを終了し、別の 1 秒間、画面を押しながら、し、[停止] ボタンをタップします。</span><span class="sxs-lookup"><span data-stu-id="48af3-232">To finish recording tap and hold the screen for another 1 second, then tap the stop button.</span></span>
4. <span data-ttu-id="48af3-233">プレビュー ボタン (青色のボタン) が表示されます、録画されたビデオが読み込まれたら、録画したビデオを見るにタップします。</span><span class="sxs-lookup"><span data-stu-id="48af3-233">Once the recorded video loads, a Preview button (blue button) will appear, tap to watch the recorded video.</span></span>
5. <span data-ttu-id="48af3-234">共有のシートを開き、カメラ ロールに保存 を選択します。</span><span class="sxs-lookup"><span data-stu-id="48af3-234">Open the Share sheet and select Save to camera roll.</span></span>

### <a name="example-scene"></a><span data-ttu-id="48af3-235">シーンの例</span><span class="sxs-lookup"><span data-stu-id="48af3-235">Example scene</span></span>

<span data-ttu-id="48af3-236">例のシーンが見つかります[HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)</span><span class="sxs-lookup"><span data-stu-id="48af3-236">An example scene can be found in [HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="48af3-237">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="48af3-237">Troubleshooting</span></span>

<span data-ttu-id="48af3-238">**Unity エディターは、HoloLens デバイスによってホストされているセッションに接続できません。**</span><span class="sxs-lookup"><span data-stu-id="48af3-238">**The Unity Editor won't connect to a session hosted by a HoloLens device**</span></span>

- <span data-ttu-id="48af3-239">これは、Windows ファイアウォールで可能性があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-239">This could be the Windows Firewall.</span></span>
- <span data-ttu-id="48af3-240">Windows ファイアウォールのオプションに移動します。</span><span class="sxs-lookup"><span data-stu-id="48af3-240">Go to Windows Firewall options.</span></span>
- <span data-ttu-id="48af3-241">アプリまたは Windows ファイアウォールを使用して機能を許可します。</span><span class="sxs-lookup"><span data-stu-id="48af3-241">Allow an app or feature through Windows Firewall.</span></span>
- <span data-ttu-id="48af3-242">すべてのインスタンスの一覧のティックで Unity エディターのドメイン、プライベートおよびパブリック。</span><span class="sxs-lookup"><span data-stu-id="48af3-242">For all instances of Unity Editor in the list tick, Domain, Private and Public.</span></span>
- <span data-ttu-id="48af3-243">Windows ファイアウォールのオプションに戻ります。</span><span class="sxs-lookup"><span data-stu-id="48af3-243">Then go back to Windows Firewall options.</span></span>
- <span data-ttu-id="48af3-244">[詳細設定] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48af3-244">Click Advanced settings.</span></span>
- <span data-ttu-id="48af3-245">[受信の規則] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48af3-245">Click Inbound Rules.</span></span>
- <span data-ttu-id="48af3-246">Unity エディターのすべてのインスタンスには、緑色のチェックが必要です。</span><span class="sxs-lookup"><span data-stu-id="48af3-246">All instances of Unity Editor should have a green tick.</span></span>
- <span data-ttu-id="48af3-247">Unity エディターのすべてのインスタンスに対して、緑のチェック マークがないです。</span><span class="sxs-lookup"><span data-stu-id="48af3-247">For any instances of Unity Editor that don't have a green tick:</span></span>
    - <span data-ttu-id="48af3-248">ダブルクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="48af3-248">Double click it.</span></span>
    - <span data-ttu-id="48af3-249">アクションでは、ダイアログは、接続を許可するを選択します。</span><span class="sxs-lookup"><span data-stu-id="48af3-249">In the action dialog select Allow the connection.</span></span>
    - <span data-ttu-id="48af3-250">[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48af3-250">Click OK.</span></span>
    - <span data-ttu-id="48af3-251">Unity エディターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="48af3-251">Restart the Unity Editor.</span></span>

<span data-ttu-id="48af3-252">**実行時に、iPhone 画面の質問「を検索するフロア…」AR マーカーは表示されません。**</span><span class="sxs-lookup"><span data-stu-id="48af3-252">**At runtime the iPhone screen says "Locating Floor..." but does not display an AR marker.**</span></span>

- <span data-ttu-id="48af3-253">水平画面ので試してくださいフロアまたはテーブルの方に iPhone カメラを指すは、iPhone を探します。</span><span class="sxs-lookup"><span data-stu-id="48af3-253">The iPhone is looking for a horizontal surface so try pointing the iPhone camera towards the floor or a table.</span></span> <span data-ttu-id="48af3-254">これによって、ARKit HoloLens と空間的に同期するために必要なサーフェスを検索します。</span><span class="sxs-lookup"><span data-stu-id="48af3-254">This will help ARKit find surfaces necessary to spatially sync with HoloLens.</span></span>

<span data-ttu-id="48af3-255">**HoloLens のカメラを有効にしません iPhone が参加を試むときに自動的にします。**</span><span class="sxs-lookup"><span data-stu-id="48af3-255">**HoloLens camera does not turn on automatically when iPhone tries to join.**</span></span>

- <span data-ttu-id="48af3-256">HoloLens と iPhone の両方が同じ Wi-fi ネットワークで実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="48af3-256">Make sure both HoloLens and iPhone are running on the same Wi-Fi network.</span></span>

<span data-ttu-id="48af3-257">**モバイル デバイス上の Spectator ビュー アプリケーションを起動するときにそのカメラ Spectator ビューの他のアプリを実行している他の hololens 有効にします。**</span><span class="sxs-lookup"><span data-stu-id="48af3-257">**When launching an Spectator View application on a mobile device, other hololens running other Spectator View apps turn on their camera**</span></span>

- <span data-ttu-id="48af3-258">Goto NewDeviceDiscovery コンポーネントと 2 つの一意の値にブロードキャスト キーおよびブロードキャストの両方のポートを変更します。</span><span class="sxs-lookup"><span data-stu-id="48af3-258">Goto the NewDeviceDiscovery component and change the both the Broadcast Key and Broadcast port to two unique values.</span></span>
- <span data-ttu-id="48af3-259">SpectatorViewDiscovery に移動し、別のセットの一意の番号に、キーのブロードキャストとブロードキャストのポートを変更します。</span><span class="sxs-lookup"><span data-stu-id="48af3-259">Go to SpectatorViewDiscovery and change the Broadcast Key and Broadcast port to another set of unique numbers.</span></span>

<span data-ttu-id="48af3-260">**Mac の Unity エディターで、HoloLens を接続できません。**</span><span class="sxs-lookup"><span data-stu-id="48af3-260">**The HoloLens won't connect with the mac Unity Editor.**</span></span>

- <span data-ttu-id="48af3-261">これは、Unity のバージョンにリンクできますが、既知の問題です。</span><span class="sxs-lookup"><span data-stu-id="48af3-261">This is a known issue which could be linked to the Unity version.</span></span> <span data-ttu-id="48af3-262">IPhone を構築する必要がありますも動作し、通常どおりに接続します。</span><span class="sxs-lookup"><span data-stu-id="48af3-262">Building to the iPhone should still work and connect as normal.</span></span>

<span data-ttu-id="48af3-263">**HoloLens カメラでは、オンが、マーカーをスキャンすることではありません。**</span><span class="sxs-lookup"><span data-stu-id="48af3-263">**The HoloLens camera turns on but is not able to scan the marker.**</span></span>

- <span data-ttu-id="48af3-264">Unity エディターの同じインスタンス (do 間終了させない Unity のビルド) を使用して、アプリケーションのすべてのバージョンを作成することを確認します。</span><span class="sxs-lookup"><span data-stu-id="48af3-264">Ensure that you build all versions of the application using the same Unity Editor instance (do not close Unity between builds).</span></span> <span data-ttu-id="48af3-265">Unity の不明な問題が原因になります。</span><span class="sxs-lookup"><span data-stu-id="48af3-265">This is due to an unknown issue with Unity.</span></span>

## <a name="spectator-view-pro"></a><span data-ttu-id="48af3-266">Spectator Pro の表示</span><span class="sxs-lookup"><span data-stu-id="48af3-266">Spectator View Pro</span></span>

![Spectator 設定の表示](images/spectatorview-300px.png)

<span data-ttu-id="48af3-268">Spectator ビューの Pro を使用して、これら 4 つのコンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="48af3-268">Using Spectator View Pro involves these four components:</span></span>
1. <span data-ttu-id="48af3-269">基づく spectator ビューを有効にするには、具体的にはビルドされたアプリ[複合現実での経験を共有](shared-experiences-in-mixed-reality.md)します。</span><span class="sxs-lookup"><span data-stu-id="48af3-269">An app built specifically to enable spectator view, which is based on [shared experiences in mixed reality](shared-experiences-in-mixed-reality.md).</span></span>
2. <span data-ttu-id="48af3-270">ソックスを着けずに HoloLens、アプリを使用してユーザー。</span><span class="sxs-lookup"><span data-stu-id="48af3-270">A user wearing HoloLens using the app.</span></span>
3. <span data-ttu-id="48af3-271">人称視点のビデオを提供する、spectator ビュー カメラ装置です。</span><span class="sxs-lookup"><span data-stu-id="48af3-271">A spectator view camera rig providing a third-person perspective video.</span></span>
4. <span data-ttu-id="48af3-272">実行しているアプリの共有エクスペリエンスおよび複合、ホログラム spectator ビューのビデオにデスクトップ PC。</span><span class="sxs-lookup"><span data-stu-id="48af3-272">A desktop PC running the shared experience app and compositing the holograms into a spectator view video.</span></span>

![Spectator ビューの Pro 設定](images/hololensspectatorview-500px.jpg) 

### <a name="use-cases"></a><span data-ttu-id="48af3-274">使用事例</span><span class="sxs-lookup"><span data-stu-id="48af3-274">Use cases</span></span>

>[!VIDEO https://www.youtube.com/embed/DgIHjxoPy_c]


<span data-ttu-id="48af3-275">*Spectator ビューは、静止画像、ビデオ クリップ、またはライブ デモになるかどうか、holographic せましょうの共有を使用できます。*</span><span class="sxs-lookup"><span data-stu-id="48af3-275">*Spectator view can be used for sharing your holographic creations, whether they're a still image, a video clip, or a live demonstration.*</span></span>


<span data-ttu-id="48af3-276">このテクノロジと連動する次の 3 つの主要なシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="48af3-276">There are three key scenarios that work well with this technology:</span></span>

<span data-ttu-id="48af3-277">**1.写真をキャプチャ**</span><span class="sxs-lookup"><span data-stu-id="48af3-277">**1. Photo capture**</span></span><br>
<span data-ttu-id="48af3-278">このテクノロジを使用して、ホログラムの高解像度のイメージをキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="48af3-278">Using this technology, you can capture high resolution images of your holograms.</span></span> <span data-ttu-id="48af3-279">これらのイメージは、イベントのマーケティング コンテンツを紹介するを潜在的なクライアントに送信または Windows Store にアプリケーションを送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="48af3-279">These images can be used to showcase content at marketing events, send to your potential clients, or even submit your application to the Windows Store.</span></span> <span data-ttu-id="48af3-280">どの写真のカメラを使用してこれらのイメージをキャプチャしたいのかを決定する、そのため、品質 DSLR カメラこともできます。</span><span class="sxs-lookup"><span data-stu-id="48af3-280">You get to decide which photo camera you would like to use to capture these images, as such you may prefer a quality DSLR camera.</span></span>


<span data-ttu-id="48af3-281">![Spectator ビュー Pro 写真キャプチャのサンプル](images/fall-350px.jpg)</span><span class="sxs-lookup"><span data-stu-id="48af3-281">![Spectator View Pro photo capture example](images/fall-350px.jpg)</span></span><br>
<span data-ttu-id="48af3-282">*写真のキャプチャの例 - 溶岩をから床面が見えるようにされます。*</span><span class="sxs-lookup"><span data-stu-id="48af3-282">*Photo capture example - making it appear the floor is made of lava.*</span></span>


<span data-ttu-id="48af3-283">**2.ビデオのキャプチャ**</span><span class="sxs-lookup"><span data-stu-id="48af3-283">**2. Video capture**</span></span><br>
<span data-ttu-id="48af3-284">ビデオは、多くの人と holographic アプリ エクスペリエンスを共有するためのメカニズムを示す最適なストーリーです。</span><span class="sxs-lookup"><span data-stu-id="48af3-284">Videos are the best story telling mechanism for sharing a holographic app experience with many people.</span></span> <span data-ttu-id="48af3-285">Spectator ビューでは、最も適したアプリを紹介する方法をカメラ、レンズは、フレームを選択できます。</span><span class="sxs-lookup"><span data-stu-id="48af3-285">Spectator view lets you choose the camera, lens, and framing that best suits how you want to showcase your app.</span></span> <span data-ttu-id="48af3-286">これは、ビデオ ハードウェアに基づくビデオ品質のコントロールで使用可能ながあります。</span><span class="sxs-lookup"><span data-stu-id="48af3-286">It puts you in control of the video quality based on the video hardware you have available.</span></span>

<span data-ttu-id="48af3-287">![Spectator ビュー Pro ビデオ キャプチャ例](images/spectatorviewvideo.gif)</span><span class="sxs-lookup"><span data-stu-id="48af3-287">![Spectator View Pro video capture example](images/spectatorviewvideo.gif)</span></span><br>
<span data-ttu-id="48af3-288">*ビデオ キャプチャ例 - 複合現実のコラボレーション エクスペリエンスを記録します。*</span><span class="sxs-lookup"><span data-stu-id="48af3-288">*Video capture example - recording a mixed reality collaboration experience.*</span></span>


<span data-ttu-id="48af3-289">**3.ライブ デモ**</span><span class="sxs-lookup"><span data-stu-id="48af3-289">**3. Live demonstrations**</span></span><br>
<span data-ttu-id="48af3-290">Spectator ビューはライブ デモに対して推奨されるアプローチ安定または制御されたカメラの位置のままです。</span><span class="sxs-lookup"><span data-stu-id="48af3-290">Spectator view is a preferred approach for live demonstrations as the camera position remains steady or controlled.</span></span> <span data-ttu-id="48af3-291">高品質なビデオ_カメラを使用するため、大きな画面向けの高品質なイメージを作成することもします。</span><span class="sxs-lookup"><span data-stu-id="48af3-291">Because you can use a high-quality video camera, you can also produce high-quality images meant for a big screen.</span></span> <span data-ttu-id="48af3-292">これは、ストリーミングが有効にするは、行で待機している一括の参加者に可能性があります、画面上のライブ デモに適したも。</span><span class="sxs-lookup"><span data-stu-id="48af3-292">This is also appropriate for streaming live demos on a screen, possibly to eager participants waiting in line for their turn.</span></span>

### <a name="comparing-video-capture-techniques"></a><span data-ttu-id="48af3-293">ビデオ キャプチャ手法の比較</span><span class="sxs-lookup"><span data-stu-id="48af3-293">Comparing video capture techniques</span></span>

<span data-ttu-id="48af3-294">[実際のキャプチャを混合](mixed-reality-capture.md)(MRC) の最初のユーザーの観点から、HoloLens のユーザーが表示されるコンポジット ビデオを提供します。</span><span class="sxs-lookup"><span data-stu-id="48af3-294">[Mixed reality capture](mixed-reality-capture.md) (MRC) provides a video composite of what the HoloLens user is seeing from a first person point-of-view.</span></span> <span data-ttu-id="48af3-295">Spectator ビューでは、ホログラムとソックスを着けずに HoloLens デバイス ユーザーの環境を表示するビデオのオブザーバーを許可する - 3 人目の観点からビデオを生成します。</span><span class="sxs-lookup"><span data-stu-id="48af3-295">Spectator view produces a video from a third-person perspective, allowing the video observer to see the environment with holograms and the user wearing a HoloLens device.</span></span> <span data-ttu-id="48af3-296">カメラの選択肢があるために、高い解像度と MRC イメージを使用する組み込み HoloLens カメラより優れた品質の画像が spectator ビューに生成もできます。</span><span class="sxs-lookup"><span data-stu-id="48af3-296">Because you have a choice of camera, spectator views can also produce higher resolution and better quality images than the built-in HoloLens camera used for MRC images.</span></span> <span data-ttu-id="48af3-297">このため、spectator ビューよりマーケティングのビデオ、Windows ストア アプリの画像やユーザー向けのライブ ビューを射影は適しています。</span><span class="sxs-lookup"><span data-stu-id="48af3-297">For this reason, spectator view is better suited for app images in the Windows Store, marketing videos, or for projecting a live view for an audience.</span></span>

<span data-ttu-id="48af3-298">![Microsoft での基調講演のプレゼンテーションで使用されるビューの Pro professional カメラを spectator](images/spectator-view-professional-red-camera-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="48af3-298">![Spectator View Pro professional camera used in Microsoft keynote presentations](images/spectator-view-professional-red-camera-300px.jpg)</span></span><br>
<span data-ttu-id="48af3-299">*Microsoft での基調講演のプレゼンテーションで使用されるビューの Pro professional カメラを spectator*</span><span class="sxs-lookup"><span data-stu-id="48af3-299">*Spectator View Pro professional camera used in Microsoft keynote presentations*</span></span>


<span data-ttu-id="48af3-300">Spectator ビューには、Microsoft HoloLens がの表示方法エクスペリエンスの対象ユーザーを非常に当初から、製品が 2015 年 1 月に発表したときの重要な要素がされました。</span><span class="sxs-lookup"><span data-stu-id="48af3-300">Spectator view has been an essential piece of how Microsoft HoloLens has presented experiences to audiences since the very beginning when the product was announced in January 2015.</span></span> <span data-ttu-id="48af3-301">Professional の設定では、多くの要求と負荷の高い価格タグを必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-301">The professional setup used had high demands and an expensive price tag to go with it.</span></span> <span data-ttu-id="48af3-302">たとえば、カメラは genlock 信号を使用して、追跡システム HoloLens と連携して正確なタイミングを確認します。</span><span class="sxs-lookup"><span data-stu-id="48af3-302">For example, the camera uses a genlock signal to ensure precise timing that coordinates with the HoloLens tracking system.</span></span> <span data-ttu-id="48af3-303">このセットアップでは、spectator ビュー カメラを移動が可能な他のユーザーが多い、HoloLens で直接開発のエクスペリエンスを一致するように安定したホログラムを維持しながら。</span><span class="sxs-lookup"><span data-stu-id="48af3-303">In this setup, moving the spectator view camera was possible while keeping holograms stable to match the experience of someone who is seeing the experience directly in HoloLens.</span></span>

<span data-ttu-id="48af3-304">Spectator ビューのオープン ソースのバージョンと引き換え全体的なセットアップのコストを大幅に削減するためにカメラのリモート テスト マシン群を移動する機能が無効です。</span><span class="sxs-lookup"><span data-stu-id="48af3-304">The open-source version of spectator view trades off the ability to move the camera rig in order to dramatically lower the cost of the overall setup.</span></span> <span data-ttu-id="48af3-305">このプロジェクトでは、剛体、HoloLens にマウントされている外部のカメラを使用して、高解像度写真の撮影と holographic Unity プロジェクトのビデオ。</span><span class="sxs-lookup"><span data-stu-id="48af3-305">This project uses an external camera rigidly mounted to a HoloLens to take high-definition pictures and video of your holographic Unity project.</span></span> <span data-ttu-id="48af3-306">**ライブ デモ、中には、カメラは、固定位置に残っている必要があります。**</span><span class="sxs-lookup"><span data-stu-id="48af3-306">**During live demonstrations, the camera should remain in a fixed position.**</span></span> <span data-ttu-id="48af3-307">カメラの動きは、ホログラム ジッターや誤差につながることができます。</span><span class="sxs-lookup"><span data-stu-id="48af3-307">Movement of the camera can lead to hologram jitter or drift.</span></span> <span data-ttu-id="48af3-308">これは、ビデオのフレームのタイミングと、PC でホログラムのレンダリングは正確に同期できないためにです。</span><span class="sxs-lookup"><span data-stu-id="48af3-308">This is because the timing of the video frame and the rendering of holograms on the PC may not be precisely synchronized.</span></span> <span data-ttu-id="48af3-309">そのため、カメラを安定した保持するか、移動を制限すると、HoloLens を着ている人が確認できるものに近い結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="48af3-309">Therefore, keeping the camera steady or limiting movement will produce a result close to what the person wearing a HoloLens can see.</span></span>

<span data-ttu-id="48af3-310">アプリを spectator ビューに対応するためには、ビルドする必要があります、[エクスペリエンスを共有](holograms-240.md)アプリ HoloLens と Unity エディターでデスクトップの両方でアプリを実行できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="48af3-310">To make your app ready for spectator view, you'll need to build a [shared experience](holograms-240.md) app and ensure the app can run on both HoloLens as well as desktop in the Unity editor.</span></span> <span data-ttu-id="48af3-311">デスクトップ バージョンのアプリには、その複合ビデオ フィード表示ホログラムに組み込まれている追加のコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="48af3-311">The desktop version of the app will have additional components built in that composite the video feed with the rendered holograms.</span></span>

## <a name="how-to-set-up-spectator-view-pro"></a><span data-ttu-id="48af3-312">Spectator ビューの Pro を設定する方法</span><span class="sxs-lookup"><span data-stu-id="48af3-312">How to set up Spectator View Pro</span></span> 

### <a name="requirements"></a><span data-ttu-id="48af3-313">必要条件</span><span class="sxs-lookup"><span data-stu-id="48af3-313">Requirements</span></span>

![Spectator ビュー Pro リモート テスト マシン群](images/spectatorviewrig-350px.jpg)

#### <a name="hardware-shopping-list"></a><span data-ttu-id="48af3-315">ハードウェアのショッピング リスト</span><span class="sxs-lookup"><span data-stu-id="48af3-315">Hardware shopping list</span></span>

<span data-ttu-id="48af3-316">以下は、ハードウェアの推奨される一覧ですが、他の互換性のある単位での実験も。</span><span class="sxs-lookup"><span data-stu-id="48af3-316">Below is a recommended list of hardware, but you can experiment with other compatible units too.</span></span> 

|<span data-ttu-id="48af3-317">ハードウェア コンポーネント</span><span class="sxs-lookup"><span data-stu-id="48af3-317">Hardware component</span></span>                                                                     |<span data-ttu-id="48af3-318">推奨</span><span class="sxs-lookup"><span data-stu-id="48af3-318">Recommendation</span></span>               | 
|:--------------------------------------------------------------------------------------|:----------------------------|
|<span data-ttu-id="48af3-319">HoloLens のエミュレーターを使用した holographic の開発に適している PC の構成</span><span class="sxs-lookup"><span data-stu-id="48af3-319">A PC configuration that works for holographic development with the HoloLens emulator</span></span>  |                              | 
|<span data-ttu-id="48af3-320">カメラを HDMI または写真をキャプチャ SDK</span><span class="sxs-lookup"><span data-stu-id="48af3-320">Camera with HDMI out or photo capture SDK</span></span>                                             | <span data-ttu-id="48af3-321">写真とビデオのキャプチャは、テストしましたが、 [Canon EOS 5 D マーク III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III)カメラ。</span><span class="sxs-lookup"><span data-stu-id="48af3-321">For photo and video capture, we have tested the [Canon EOS 5D Mark III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III) camera.</span></span> <span data-ttu-id="48af3-322">ライブ デモをテストしましたが、 [Blackmagic デザイン運用カメラ 4 K](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k)します。</span><span class="sxs-lookup"><span data-stu-id="48af3-322">For live demonstrations, we have tested the [Blackmagic Design Production Camera 4K](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k).</span></span><br><br><span data-ttu-id="48af3-323">(例: GoPro) out HDMI でカメラが動作する必要がありますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="48af3-323">Note, any camera with HDMI out (e.g. GoPro) should work.</span></span> <span data-ttu-id="48af3-324">ビデオの多くを使用して、 [Canon EF 14 mm f/2.8 L II USM: ultra Wide 角度固定レンズ](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q)がニーズを満たすカメラのレンズを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-324">Many of our videos use the [Canon EF 14mm f/2.8L II USM Ultra-Wide Angle Fixed Lens](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q), but you should choose a camera lens that meets your needs.</span></span> | 
|<span data-ttu-id="48af3-325">キャプチャ、リモート テスト マシン群を調整して合成シーンをプレビューするには、カメラからフレームの色を取得する PC のカード</span><span class="sxs-lookup"><span data-stu-id="48af3-325">Capture card for your PC to get color frames from your camera to calibrate your rig and preview your composite scene</span></span> |  <span data-ttu-id="48af3-326">テストしましたが、 [Blackmagic デザイン強度 Pro 4 K キャプチャ カード](https://www.amazon.com/dp/B00U3QNP7Q)します。</span><span class="sxs-lookup"><span data-stu-id="48af3-326">We have tested the [Blackmagic Design Intensity Pro 4K capture card](https://www.amazon.com/dp/B00U3QNP7Q).</span></span> | 
|<span data-ttu-id="48af3-327">ケーブル (複数)</span><span class="sxs-lookup"><span data-stu-id="48af3-327">Cables</span></span>                                                                                 |  <span data-ttu-id="48af3-328">[ミニ HDMI を HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00)キャプチャ カード、カメラを接続します。</span><span class="sxs-lookup"><span data-stu-id="48af3-328">[HDMI to Mini HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00) for attaching your camera to your capture card.</span></span> <span data-ttu-id="48af3-329">カメラに合った HDMI フォーム ファクターを購入することを確認します。</span><span class="sxs-lookup"><span data-stu-id="48af3-329">Ensure you purchase an HDMI form factor that fits your camera.</span></span> <span data-ttu-id="48af3-330">(GoPro は、たとえば、経由で出力[マイクロ HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1))。</span><span class="sxs-lookup"><span data-stu-id="48af3-330">(GoPro, for instance, outputs over [Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1).)</span></span><br><br><span data-ttu-id="48af3-331">[HDMI ケーブル](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1)複合プレビュー モニターまたはテレビでフィードを表示します。</span><span class="sxs-lookup"><span data-stu-id="48af3-331">[HDMI cable](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1) for viewing the composite feed on a preview monitor or television</span></span> | 
|<span data-ttu-id="48af3-332">カメラに接続、HoloLens、アルミニウム角かっこを加工します。</span><span class="sxs-lookup"><span data-stu-id="48af3-332">Machined aluminum bracket to connect your HoloLens to the camera.</span></span> | [<span data-ttu-id="48af3-333">アルミニウム角かっこ</span><span class="sxs-lookup"><span data-stu-id="48af3-333">Aluminum bracket</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/HoloLens_Mount.stp)   | 
|<span data-ttu-id="48af3-334">3D では、HoloLens のマウントをカメラ hotshoe に接続するアダプターを印刷します。</span><span class="sxs-lookup"><span data-stu-id="48af3-334">3D printed adapter to connect the HoloLens mount to the camera hotshoe.</span></span>| [<span data-ttu-id="48af3-335">3D 印刷アダプター</span><span class="sxs-lookup"><span data-stu-id="48af3-335">3D printed adapter</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/Mount_Adapter.stl)  | 
|<span data-ttu-id="48af3-336">Hotshoe fastener hotshoe アダプターをマウントするには</span><span class="sxs-lookup"><span data-stu-id="48af3-336">Hotshoe fastener to mount the hotshoe adapter</span></span>                                       |  [<span data-ttu-id="48af3-337">Hotshoe Fastener</span><span class="sxs-lookup"><span data-stu-id="48af3-337">Hotshoe Fastener</span></span>](https://www.amazon.com/Fotasy-SCX2-Adapter-Premier-Cleaning/dp/B00HPAPFNU/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) | 
|<span data-ttu-id="48af3-338">さまざまなナットやボルト、ツール</span><span class="sxs-lookup"><span data-stu-id="48af3-338">Assorted nuts, bolts, and tools</span></span>                                                |  [<span data-ttu-id="48af3-339">1/4-20"ナット</span><span class="sxs-lookup"><span data-stu-id="48af3-339">1/4-20" Nuts</span></span>](https://www.amazon.com/Hillman-Group-150003-20-Inch-100-Pack/dp/B000BPEPNW/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img)<br>[<span data-ttu-id="48af3-340">1/4-20"× 3/4"ボルト</span><span class="sxs-lookup"><span data-stu-id="48af3-340">1/4-20" x 3/4" Bolts</span></span>](https://www.amazon.com/Hard-Find-Fastener-014973100032-4-20-Inch/dp/B004S6RZPK/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) <br>[<span data-ttu-id="48af3-341">7/16 ナット ドライバー</span><span class="sxs-lookup"><span data-stu-id="48af3-341">7/16 Nut Driver</span></span>](https://www.amazon.com/Klein-Tools-630-7-Cushion-Grip-Hollow-Shank/dp/B000BPG4CW/ref=sr_1_1?ie=UTF8&qid=1479853212&sr=8-1)<br>[<span data-ttu-id="48af3-342">T15 Torx</span><span class="sxs-lookup"><span data-stu-id="48af3-342">T15 Torx</span></span>](https://www.amazon.com/Stanley-60-011-Standard-Torx-Screwdriver/dp/B000KFXDWW/ref=sr_1_1?ie=UTF8&qid=1479853303&sr=8-1)<br>[<span data-ttu-id="48af3-343">T7 Torx</span><span class="sxs-lookup"><span data-stu-id="48af3-343">T7 Torx</span></span>](https://www.amazon.com/SE-7542ST-6-Piece-Professional-Screwdriver/dp/B000ST3K3W/ref=sr_1_1?ie=UTF8&qid=1479853479&sr=8-1) | 

#### <a name="software-components"></a><span data-ttu-id="48af3-344">ソフトウェア コンポーネント</span><span class="sxs-lookup"><span data-stu-id="48af3-344">Software components</span></span>

1. <span data-ttu-id="48af3-345">ソフトウェアをダウンロード、 [spectator ビュー用の GitHub プロジェクト](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)します。</span><span class="sxs-lookup"><span data-stu-id="48af3-345">Software downloaded from the [GitHub project for spectator view](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView).</span></span>
2. <span data-ttu-id="48af3-346">[Blackmagic キャプチャ カード SDK](https://www.blackmagicdesign.com/support)\。</span><span class="sxs-lookup"><span data-stu-id="48af3-346">[Blackmagic Capture Card SDK](https://www.blackmagicdesign.com/support).\\</span></span>
 <span data-ttu-id="48af3-347">デスクトップのビデオ Developer「最新のダウンロード」で SDK を検索します。</span><span class="sxs-lookup"><span data-stu-id="48af3-347">Search for Desktop Video Developer SDK in "Latest Downloads".</span></span>
3. <span data-ttu-id="48af3-348">[Blackmagic デスクトップ ビデオ ランタイム](https://www.blackmagicdesign.com/support)\。</span><span class="sxs-lookup"><span data-stu-id="48af3-348">[Blackmagic Desktop Video Runtime](https://www.blackmagicdesign.com/support).\\</span></span>
 <span data-ttu-id="48af3-349">「最新版のダウンロード」でデスクトップのビデオのソフトウェア更新プログラムを検索します \。</span><span class="sxs-lookup"><span data-stu-id="48af3-349">Search for Desktop Video Software Update in "Latest Downloads".\\</span></span>
 <span data-ttu-id="48af3-350">バージョン番号と一致する SDK のバージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="48af3-350">Ensure the version number matches the SDK version.</span></span>
4. <span data-ttu-id="48af3-351">[OpenCV 3.1](https://opencv.org/releases.html)調整または Blackmagic キャプチャのカードがないビデオ キャプチャします。</span><span class="sxs-lookup"><span data-stu-id="48af3-351">[OpenCV 3.1](https://opencv.org/releases.html) For calibration or video capture without the Blackmagic capture card.</span></span>
5. <span data-ttu-id="48af3-352">[Canon SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) (省略可能). \\</span><span class="sxs-lookup"><span data-stu-id="48af3-352">[Canon SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) (Optional).\\</span></span>
 <span data-ttu-id="48af3-353">Canon カメラを使用しているし、Canon SDK へのアクセスがある場合より高い解像度のイメージを実行する PC にカメラを使用できます。</span><span class="sxs-lookup"><span data-stu-id="48af3-353">If you are using a Canon camera and have access to the Canon SDK, you can tether your camera to your PC to take higher resolution images.</span></span>
6. <span data-ttu-id="48af3-354">Holographic アプリ開発の unity \。</span><span class="sxs-lookup"><span data-stu-id="48af3-354">Unity for your holographic app development.\\</span></span>
 <span data-ttu-id="48af3-355">OSS プロジェクトでは、サポートされているバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="48af3-355">Supported version can be found in the OSS project.</span></span>
7. <span data-ttu-id="48af3-356">最新の更新プログラムの visual Studio 2015。</span><span class="sxs-lookup"><span data-stu-id="48af3-356">Visual Studio 2015 with latest updates.</span></span>

### <a name="building-your-own-spectator-view-pro-camera"></a><span data-ttu-id="48af3-357">Spectator ビュー Pro カメラの構築</span><span class="sxs-lookup"><span data-stu-id="48af3-357">Building your own Spectator View Pro camera</span></span>

<span data-ttu-id="48af3-358">**通知および免責事項:** 基本的な (など、HoloLens「spectator ビュー」の設定に限定されません)、HoloLens のハードウェアの変更を行うときに安全に関する注意事項に従って常にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-358">**NOTICE & DISCLAIMER:** When making modifications to your HoloLens hardware (including, but not limited to, setting up your HoloLens for "spectator view") basic safety precautions should always be observed.</span></span> <span data-ttu-id="48af3-359">すべての変更を加える前に、すべての手順については、マニュアルを読み取る。</span><span class="sxs-lookup"><span data-stu-id="48af3-359">Read all instructions and manuals before making any modifications.</span></span> <span data-ttu-id="48af3-360">すべての手順し、ツールを使用して、指示に従ってユーザーの責任になります。</span><span class="sxs-lookup"><span data-stu-id="48af3-360">It is your responsibility to follow all instructions and use tools as directed.</span></span> <span data-ttu-id="48af3-361">購入または制限付き保証または保証の免責、HoloLens のライセンスを取得した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-361">You may have purchased or licensed your HoloLens with a limited warranty or no warranty.</span></span> <span data-ttu-id="48af3-362">該当するをお読みください[HoloLens の使用許諾契約書または使用条件および販売](https://www.microsoft.com/hololens/support/warranty)保証オプションについて理解します。</span><span class="sxs-lookup"><span data-stu-id="48af3-362">Please read your applicable [HoloLens License Agreement or Terms of Use and Sale](https://www.microsoft.com/hololens/support/warranty) to understand your warranty options.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/aKX8UMejtWc]

#### <a name="rig-assembly"></a><span data-ttu-id="48af3-363">リモート テスト マシン群のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="48af3-363">Rig Assembly</span></span>

<span data-ttu-id="48af3-364">![HoloLens と DSLR カメラに組み立てられた Spectator ビュー Pro 装置です。](images/assembly.gif)</span><span class="sxs-lookup"><span data-stu-id="48af3-364">![Assembled Spectator View Pro rig with HoloLens and DSLR camera.](images/assembly.gif)</span></span><br>
<span data-ttu-id="48af3-365">*HoloLens と DSLR カメラに組み立てられた Spectator ビューの Pro を発する*</span><span class="sxs-lookup"><span data-stu-id="48af3-365">*Assembled Spectator View Pro rig with HoloLens and DSLR camera*</span></span>


* <span data-ttu-id="48af3-366">T7 ドライバーを使用して、HoloLens から、ヘッドバンドを削除します。</span><span class="sxs-lookup"><span data-stu-id="48af3-366">Use a T7 screwdriver to remove the headband from the HoloLens.</span></span> <span data-ttu-id="48af3-367">ねじが疎、もう一方の側からのクリップでそれらを開けます。</span><span class="sxs-lookup"><span data-stu-id="48af3-367">Once the screws are loose, poke them out with a paperclip from the other side.</span></span>
* <span data-ttu-id="48af3-368">内側にネジ cap を削除小型マイナス ドライバーでの HoloLens のハイパーバイザーの表面。</span><span class="sxs-lookup"><span data-stu-id="48af3-368">Remove the screw cap on the inside front of the HoloLens visor with a small flat head screwdriver.</span></span>
* <span data-ttu-id="48af3-369">T15 ドライバーを使用して、削除、HoloLens の角かっこから小さな torx ボルトを削除して添付ファイルのフック形します。</span><span class="sxs-lookup"><span data-stu-id="48af3-369">Use a T15 screwdriver to remove the small torx bolts from the HoloLens bracket to remove the U and Hook-shaped attachments.</span></span>
* <span data-ttu-id="48af3-370">角かっこ、角かっこの前面の 3-d 図形を使用して、公開されている、ハイパーバイザーの内側の穴に通します、HoloLens を配置します。</span><span class="sxs-lookup"><span data-stu-id="48af3-370">Place the HoloLens on the bracket, lining up the exposed hole on the inside of the visor with the extrusion on the front of the bracket.</span></span> <span data-ttu-id="48af3-371">角かっこの下部にあるピンでインプレース HoloLens の腕を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-371">The HoloLens' arms should be kept in place by the pins on the bottom of the bracket.</span></span>
* <span data-ttu-id="48af3-372">再アタッチして、HoloLens、角かっこをセキュリティで保護するフックの形の添付ファイル。</span><span class="sxs-lookup"><span data-stu-id="48af3-372">Reattach the U and Hook-shaped attachments to secure the HoloLens to the bracket.</span></span>
* <span data-ttu-id="48af3-373">カメラの hotshoe に hotshoe fastener をアタッチします。</span><span class="sxs-lookup"><span data-stu-id="48af3-373">Attach the hotshoe fastener to the hotshoe of your camera.</span></span>
* <span data-ttu-id="48af3-374">マウントのアダプターを hotshoe fastener にアタッチします。</span><span class="sxs-lookup"><span data-stu-id="48af3-374">Attach the mount adapter to the hotshoe fastener.</span></span>
* <span data-ttu-id="48af3-375">狭い側が転送に接続するためのアダプターとカメラのレンズに並列的に回転させます。</span><span class="sxs-lookup"><span data-stu-id="48af3-375">Rotate the adapter so the narrow side is facing forward and parallel to the camera's lens.</span></span>
* <span data-ttu-id="48af3-376">7/16 ナット ドライバーを使用して、1/4"ナッツと場所のアダプターをセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="48af3-376">Secure the adapter in place with a 1/4" nut using the 7/16 nut driver.</span></span>
* <span data-ttu-id="48af3-377">HoloLens のハイパーバイザーの前面カメラのレンズの前にできるだけ近いので、アダプターに対して角かっこを配置します。</span><span class="sxs-lookup"><span data-stu-id="48af3-377">Position the bracket against the adapter so the front of the HoloLens' visor is as close as possible to the front of the camera's lens.</span></span>
* <span data-ttu-id="48af3-378">4 の 1/4"とは比べ物 7/16 ナット ドライバーを使用すると、角かっこをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="48af3-378">Attach the bracket with 4 1/4" nuts and bolts using the 7/16 nut driver.</span></span>

#### <a name="pc-setup"></a><span data-ttu-id="48af3-379">PC のセットアップ</span><span class="sxs-lookup"><span data-stu-id="48af3-379">PC Setup</span></span>
* <span data-ttu-id="48af3-380">ソフトウェアのコンポーネント セクションからソフトウェアをインストールします。</span><span class="sxs-lookup"><span data-stu-id="48af3-380">Install the software from the software components section.</span></span>
* <span data-ttu-id="48af3-381">マザーボード上の開いている PCIe スロットにキャプチャ カードを追加します。</span><span class="sxs-lookup"><span data-stu-id="48af3-381">Add the capture card to an open PCIe slot on your motherboard.</span></span>
* <span data-ttu-id="48af3-382">外部の HDMI スロットに、カメラからの HDMI ケーブル (HDMI) 上でキャプチャ カード。</span><span class="sxs-lookup"><span data-stu-id="48af3-382">Plug an HDMI cable from your camera to the outer HDMI slot (HDMI-In) on the capture card.</span></span>
* <span data-ttu-id="48af3-383">省略可能なプレビュー モニターにキャプチャ カードで center HDMI スロット (HDMI アウト) から HDMI ケーブルを接続します。</span><span class="sxs-lookup"><span data-stu-id="48af3-383">Plug an HDMI cable from the center HDMI slot (HDMI-Out) on the capture card to an optional preview monitor.</span></span>

#### <a name="camera-setup"></a><span data-ttu-id="48af3-384">カメラのセットアップ</span><span class="sxs-lookup"><span data-stu-id="48af3-384">Camera Setup</span></span>
* <span data-ttu-id="48af3-385">ビデオ モードをカメラが 3:4 写真の解像度、トリミングではなく、完全な解像度 1920 x 1080 で出力には、それを変更します。</span><span class="sxs-lookup"><span data-stu-id="48af3-385">Change your camera to Video Mode so it outputs at the full 1920x1080 resolution rather than a cropped 3:4 photo resolution.</span></span>
* <span data-ttu-id="48af3-386">カメラの HDMI 設定を有効にする見つけて**ミラーリング**または**デュアル モニター**します。</span><span class="sxs-lookup"><span data-stu-id="48af3-386">Find your camera's HDMI settings and enable **Mirroring** or **Dual Monitor**.</span></span>
* <span data-ttu-id="48af3-387">1080 P. に出力解像度を設定します。</span><span class="sxs-lookup"><span data-stu-id="48af3-387">Set the output resolution to 1080P.</span></span>
* <span data-ttu-id="48af3-388">オフにする**ビューの画面にライブ**画面のオーバーレイは、フィード、合成には表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="48af3-388">Turn off **Live View On Screen Display** so any screen overlays do not appear in the composite feed.</span></span>
* <span data-ttu-id="48af3-389">カメラの**ライブ ビュー**します。</span><span class="sxs-lookup"><span data-stu-id="48af3-389">Turn on your camera's **Live View**.</span></span>
* <span data-ttu-id="48af3-390">使用する場合、 **Canon SDK** flash 単位を使用して、無効にして**サイレント LV 撮影**します。</span><span class="sxs-lookup"><span data-stu-id="48af3-390">If using the **Canon SDK** and would like to use a flash unit, disable **Silent LV Shoot**.</span></span>
* <span data-ttu-id="48af3-391">外部の HDMI スロットにカメラからの HDMI ケーブル (HDMI) 上でキャプチャ カード。</span><span class="sxs-lookup"><span data-stu-id="48af3-391">Plug an HDMI cable from the camera to the outer HDMI slot (HDMI-In) on the capture card.</span></span>

#### <a name="calibration"></a><span data-ttu-id="48af3-392">調整</span><span class="sxs-lookup"><span data-stu-id="48af3-392">Calibration</span></span>

<span data-ttu-id="48af3-393">Spectator ビュー リモート テスト マシン群を設定した後、HoloLens にカメラの位置と回転のオフセットを取得するために調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-393">After setting up your spectator view rig, you must calibrate in order to get the position and rotation offset of your camera to your HoloLens.</span></span>
* <span data-ttu-id="48af3-394">Calibration\Calibration.sln の下の調整の Visual Studio ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="48af3-394">Open the Calibration Visual Studio solution under Calibration\Calibration.sln.</span></span>
* <span data-ttu-id="48af3-395">このソリューションでは、ファイル dependencies.props inc の場所については、サード パーティのソースのマクロを作成します。 これが表示されます。</span><span class="sxs-lookup"><span data-stu-id="48af3-395">In this solution, you will find the file dependencies.props which creates macros for the inc locations of the 3rd party sources.</span></span>
* <span data-ttu-id="48af3-396">このファイルを更新する場所をインストールした OpenCV 3.1、Blackmagic SDK、および Canon SDK (該当する場合)</span><span class="sxs-lookup"><span data-stu-id="48af3-396">Update this file with the location you installed OpenCV 3.1, the Blackmagic SDK, and the Canon SDK (if applicable)</span></span>

<span data-ttu-id="48af3-397">![Visual Studio での依存関係の場所のスナップショット](images/dependencies-600px.png)</span><span class="sxs-lookup"><span data-stu-id="48af3-397">![Dependency locations snapshot in Visual Studio](images/dependencies-600px.png)</span></span><br>
<span data-ttu-id="48af3-398">*Visual Studio での依存関係の場所のスナップショット*</span><span class="sxs-lookup"><span data-stu-id="48af3-398">*Dependency locations snapshot in Visual Studio*</span></span>


* <span data-ttu-id="48af3-399">フラット、剛体の画面で、調整パターン Calibration\CalibrationPatterns\2_66_grid_FULL.png を出力します。</span><span class="sxs-lookup"><span data-stu-id="48af3-399">Print out the calibration pattern Calibration\CalibrationPatterns\2_66_grid_FULL.png on a flat, rigid surface.</span></span>
* <span data-ttu-id="48af3-400">お使いの PC に、HoloLens を USB 経由で接続します。</span><span class="sxs-lookup"><span data-stu-id="48af3-400">Plug your HoloLens into your PC over USB.</span></span>
* <span data-ttu-id="48af3-401">プリプロセッサの定義を更新**HOLOLENS_USER**と**HOLOLENS_PW**で**stdafx.h** HoloLens のデバイス ポータルの資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="48af3-401">Update the preprocessor definitions **HOLOLENS_USER** and **HOLOLENS_PW** in **stdafx.h** with your HoloLens' device portal credentials.</span></span>
* <span data-ttu-id="48af3-402">HDMI 経由でキャプチャ カード、カメラを接続し、オンにします。</span><span class="sxs-lookup"><span data-stu-id="48af3-402">Attach your camera to your capture card over HDMI and turn it on.</span></span>
* <span data-ttu-id="48af3-403">調整のソリューションを実行します。</span><span class="sxs-lookup"><span data-stu-id="48af3-403">Run the Calibration solution.</span></span>
* <span data-ttu-id="48af3-404">このようなビューを囲むチェッカー ボード パターンを移動します。</span><span class="sxs-lookup"><span data-stu-id="48af3-404">Move the checkerboard pattern around the view like this:</span></span>

<span data-ttu-id="48af3-405">![Spectator ビュー Pro リモート テスト マシン群の調整](images/calibration.gif)</span><span class="sxs-lookup"><span data-stu-id="48af3-405">![Calibrating the Spectator View Pro rig](images/calibration.gif)</span></span><br>
<span data-ttu-id="48af3-406">*Spectator ビュー Pro リモート テスト マシン群の調整*</span><span class="sxs-lookup"><span data-stu-id="48af3-406">*Calibrating the Spectator View Pro rig*</span></span>


* <span data-ttu-id="48af3-407">チェッカーがビューに表示するとき、画像が自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="48af3-407">A picture will automatically be taken when a checkerboard is in view.</span></span> <span data-ttu-id="48af3-408">[次へ] の姿勢を進める前に、HoloLens のハイパーバイザー上の白いライトを探します。</span><span class="sxs-lookup"><span data-stu-id="48af3-408">Look for the white light on the HoloLens' visor before advancing to the next pose.</span></span>
* <span data-ttu-id="48af3-409">完了したら、次のようにキーを押します**Enter**調整でアプリを作成するフォーカスで、 **CalibrationData.txt**ファイル。</span><span class="sxs-lookup"><span data-stu-id="48af3-409">When finished, press **Enter** with the Calibration app in focus to create a **CalibrationData.txt** file.</span></span>
* <span data-ttu-id="48af3-410">このファイルに保存されます**Documents\CalibrationFiles\CalibrationData.txt**</span><span class="sxs-lookup"><span data-stu-id="48af3-410">This file will be saved to **Documents\CalibrationFiles\CalibrationData.txt**</span></span>
* <span data-ttu-id="48af3-411">このファイルを調整データが正確かどうかを検査します。</span><span class="sxs-lookup"><span data-stu-id="48af3-411">Inspect this file to see if your calibration data is accurate:</span></span>
   * <span data-ttu-id="48af3-412">**DSLR RMS** 0 に近いする必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-412">**DSLR RMS** should be close to 0.</span></span>
   * <span data-ttu-id="48af3-413">**HoloLens RMS** 0 に近いする必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-413">**HoloLens RMS** should be close to 0.</span></span>
   * <span data-ttu-id="48af3-414">**ステレオ RMS**が 20 50、これは許容可能なために、2 つのカメラの視野が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-414">**Stereo RMS** may be 20-50, this is acceptable since the field of view between the two cameras may be different.</span></span>
   * <span data-ttu-id="48af3-415">**翻訳**接続されたカメラのレンズを HoloLens のカメラからの距離です。</span><span class="sxs-lookup"><span data-stu-id="48af3-415">**Translation** is the distance from the HoloLens' camera to the attached camera's lens.</span></span> <span data-ttu-id="48af3-416">これは、メーターです。</span><span class="sxs-lookup"><span data-stu-id="48af3-416">This is in meters.</span></span>
   * <span data-ttu-id="48af3-417">**回転**identity 近づく必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-417">**Rotation** should be close to identity.</span></span>
   * <span data-ttu-id="48af3-418">**DSLR_fov** y の値は、レンズの焦点距離と、カメラの本文のトリミング要素から予想される垂直ビューのフィールドの近くにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-418">**DSLR_fov** y value should be close to the vertical field of view expected from your lens' focal length and any camera body crop factor.</span></span>
* <span data-ttu-id="48af3-419">意味を理解する上記の値のいずれかが表示されない場合の再補正します。</span><span class="sxs-lookup"><span data-stu-id="48af3-419">If any of the above values do not appear to make sense, recalibrate.</span></span>
* <span data-ttu-id="48af3-420">このファイルのコピー、**資産**Unity プロジェクトのディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="48af3-420">Copy this file to the **Assets** directory in your Unity project.</span></span>

### <a name="compositor"></a><span data-ttu-id="48af3-421">Compositor</span><span class="sxs-lookup"><span data-stu-id="48af3-421">Compositor</span></span>

<span data-ttu-id="48af3-422">コンポジターが Unity エディターのウィンドウとして実行される Unity 拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="48af3-422">The compositor is a Unity extension that runs as a window in the Unity editor.</span></span> <span data-ttu-id="48af3-423">これを有効にするには、コンポジター Visual Studio ソリューションまず必要がありますを構築します。</span><span class="sxs-lookup"><span data-stu-id="48af3-423">To enable this, the Compositor Visual Studio solution first needs to be built.</span></span>
* <span data-ttu-id="48af3-424">Compositor\Compositor.sln コンポジターの Visual Studio ソリューションを開く</span><span class="sxs-lookup"><span data-stu-id="48af3-424">Open the Compositor Visual Studio solution under Compositor\Compositor.sln</span></span>
* <span data-ttu-id="48af3-425">上記の調整のソリューションと同じ条件では、dependencies.props を更新します。</span><span class="sxs-lookup"><span data-stu-id="48af3-425">Update dependencies.props with the same criteria from the Calibration solution above.</span></span> <span data-ttu-id="48af3-426">調整手順を実行する場合、このファイルは既に更新されました。</span><span class="sxs-lookup"><span data-stu-id="48af3-426">If you followed the calibration steps, this file will already have been updated.</span></span>
* <span data-ttu-id="48af3-427">リリースと Unity のバージョンのアーキテクチャに合致するアーキテクチャ ソリューション全体をビルドします。</span><span class="sxs-lookup"><span data-stu-id="48af3-427">Build the entire solution as Release and the architecture that matches your Unity version's architecture.</span></span> <span data-ttu-id="48af3-428">不明な場合に、x86 と x64 の両方をビルドします。</span><span class="sxs-lookup"><span data-stu-id="48af3-428">If in doubt, build both x86 and x64.</span></span>
* <span data-ttu-id="48af3-429">X64 用のソリューションをビルドした場合は、HoloLens 上で実行されますので、x86 として SpatialPerceptionHelper プロジェクトをビルドもします。</span><span class="sxs-lookup"><span data-stu-id="48af3-429">If you built the solution for x64, also build the SpatialPerceptionHelper project as x86 since it will run on the HoloLens.</span></span>
* <span data-ttu-id="48af3-430">アプリケーションが実行されている場合は、Unity を閉じます。</span><span class="sxs-lookup"><span data-stu-id="48af3-430">Close Unity if it is running your application.</span></span> <span data-ttu-id="48af3-431">Unity は、実行時に Dll が変更された場合は再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-431">Unity needs to be relaunched if DLLs are changed at runtime.</span></span>
* <span data-ttu-id="48af3-432">Unity プロジェクトにこのソリューションからビルドされた Dll をコピーする Compositor\CopyDLL.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="48af3-432">Run Compositor\CopyDLL.cmd to copy the DLLs built from this solution to your Unity project.</span></span> <span data-ttu-id="48af3-433">このスクリプトは、含まれているサンプル プロジェクトに Dll をコピーします。</span><span class="sxs-lookup"><span data-stu-id="48af3-433">This script will copy the DLLs to the included sample project.</span></span> <span data-ttu-id="48af3-434">独自のプロジェクトを設定した後もコピーして、プロジェクトの Assets ディレクトリを指すコマンドライン引数を指定して CopyDLL を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="48af3-434">Once you have your own project set up, you can run CopyDLL with a command line argument pointing to your project's Assets directory to copy there as well.</span></span>
* <span data-ttu-id="48af3-435">サンプルの Unity アプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="48af3-435">Launch the sample Unity app.</span></span>

### <a name="unity-app"></a><span data-ttu-id="48af3-436">Unity アプリ</span><span class="sxs-lookup"><span data-stu-id="48af3-436">Unity app</span></span>

<span data-ttu-id="48af3-437">Unity エディターのウィンドウとして、コンポジターが実行されます。</span><span class="sxs-lookup"><span data-stu-id="48af3-437">The compositor runs as a window in the Unity Editor.</span></span> <span data-ttu-id="48af3-438">含まれているサンプル プロジェクトには、spectator 表示を 1 回のコンポジターの Dll がコピー操作にするよう設定すべてが含まれます。</span><span class="sxs-lookup"><span data-stu-id="48af3-438">The included sample project has everything set up to work with spectator view once the compositor DLLs are copied.</span></span>

<span data-ttu-id="48af3-439">Spectator ビューが、アプリケーションとして実行する必要があります、[エクスペリエンスを共有](holograms-240.md)します。</span><span class="sxs-lookup"><span data-stu-id="48af3-439">Spectator view requires the application to be run as a [shared experience](holograms-240.md).</span></span> <span data-ttu-id="48af3-440">つまり、HoloLens で発生するアプリケーションの状態の変更は、Unity でも実行されているアプリを更新するネットワーク経由で接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-440">This means that any application state changes that happen on the HoloLens need to be networked to update the app running in Unity too.</span></span>

<span data-ttu-id="48af3-441">新しい Unity プロジェクトから開始する場合は最初にいくつかの設定を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-441">If starting from a new Unity project, you will need to do some setup first:</span></span>
* <span data-ttu-id="48af3-442">コピー**資産/アドオン/HolographicCameraRig**をプロジェクトにサンプル プロジェクトから。</span><span class="sxs-lookup"><span data-stu-id="48af3-442">Copy **Assets/Addons/HolographicCameraRig** from the sample project to your project.</span></span>
* <span data-ttu-id="48af3-443">最新の MixedRealityToolkit をプロジェクトに追加を含む**共有**、 **csc.rsp**、 **gmcs.rsp**、および**smcs.rsp**します。</span><span class="sxs-lookup"><span data-stu-id="48af3-443">Add the latest MixedRealityToolkit to your project, including **Sharing**, **csc.rsp**, **gmcs.rsp**, and **smcs.rsp**.</span></span>
* <span data-ttu-id="48af3-444">追加、 **CalibrationData.txt** Assets ディレクトリにファイル。</span><span class="sxs-lookup"><span data-stu-id="48af3-444">Add your **CalibrationData.txt** file to your Assets directory.</span></span>

![Unity のアセットのディレクトリのスナップショット](images/files-400px.png)

* <span data-ttu-id="48af3-446">追加、 **HolographicCameraRig\Prefabs\SpectatorViewManager** prefab シーンにし、フィールドに入力します。</span><span class="sxs-lookup"><span data-stu-id="48af3-446">Add the **HolographicCameraRig\Prefabs\SpectatorViewManager** prefab to your scene and fill in the fields:</span></span>
   * <span data-ttu-id="48af3-447">**HolographicCameraManager** HolographicCameraRig プレハブ ディレクトリから HolographicCameraManager プレハブを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-447">**HolographicCameraManager** should be populated with the HolographicCameraManager prefab from the HolographicCameraRig prefab directory.</span></span>
   * <span data-ttu-id="48af3-448">**アンカー** HolographicCameraRig プレハブ ディレクトリからアンカー プレハブを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-448">**Anchor** should be populated with the Anchor prefab from the HolographicCameraRig prefab directory.</span></span>
   * <span data-ttu-id="48af3-449">**共有**MixedRealityToolkit から共有プレハブを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-449">**Sharing** should be populated with the Sharing prefab from the MixedRealityToolkit.</span></span>
   * <span data-ttu-id="48af3-450">注:プロジェクト階層で既にがあるこれらのプレハブの場合はこれらのものではなく既存のプレハブが使用されます。</span><span class="sxs-lookup"><span data-stu-id="48af3-450">Note: If any of these prefabs already exist in your project hierarchy, the existing prefabs will be used instead of these ones.</span></span>
   * <span data-ttu-id="48af3-451">**Spectator ビュー IP** spectator ビュー リモート テスト マシン群にアタッチされている、HoloLens の ip アドレスにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-451">**Spectator View IP** should be the IP of your HoloLens attached to your spectator view rig.</span></span>
   * <span data-ttu-id="48af3-452">**共有サービスの IP** MixedRealityToolkit SharingService を実行している PC の ip アドレスにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-452">**Sharing Service IP** should be the IP of the PC running the MixedRealityToolkit SharingService.</span></span>
   * <span data-ttu-id="48af3-453">省略可能: 複数の spectator が複数の PC に接続されているリモート テスト マシン群を表示した場合の**ローカル コンピューターの IP** spectator ビューのリモート テスト マシン群が通信する PC に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-453">Optional: If you have multiple spectator view rigs attached to multiple PC's, **Local Computer IP** should be set with the PC the spectator view rig will communicate with.</span></span>

![Unity で spectator ビュー マネージャーのプロパティ](images/spectatorviewmanager-500px.png)

* <span data-ttu-id="48af3-455">開始、MixedRealityToolkit**共有サービス**</span><span class="sxs-lookup"><span data-stu-id="48af3-455">Start the MixedRealityToolkit **Sharing Service**</span></span>
* <span data-ttu-id="48af3-456">ビルドおよび spectator ビューのリモート テスト マシン群に接続されている、HoloLens に D3D の UWP アプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="48af3-456">Build and deploy the app as a D3D UWP to the HoloLens attached to the spectator view rig.</span></span>
* <span data-ttu-id="48af3-457">エクスペリエンスで他の HoloLens デバイスにアプリをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="48af3-457">Deploy the app to any other HoloLens devices in the experience.</span></span>
* <span data-ttu-id="48af3-458">チェック、**バック グラウンドで実行**下のチェック ボックス**編集/プロジェクトの設定/プレーヤー**します。</span><span class="sxs-lookup"><span data-stu-id="48af3-458">Check the **Run In Background** checkbox under **edit/project settings/player**.</span></span>

![Unity で設定をバック グラウンドで実行します。](images/run-in-bg-400px.png)
* <span data-ttu-id="48af3-460">コンポジターのウィンドウを起動**コンポジター/Spectator ビュー**</span><span class="sxs-lookup"><span data-stu-id="48af3-460">Launch the compositor window under **Spectator View/Compositor**</span></span>

![Unity で spectator ビューのコンポジターの表示](images/compositor-500px.png)

* <span data-ttu-id="48af3-462">このウィンドウを使用するできます。</span><span class="sxs-lookup"><span data-stu-id="48af3-462">This window allows you to:</span></span>
   * <span data-ttu-id="48af3-463">ビデオの録画を開始します。</span><span class="sxs-lookup"><span data-stu-id="48af3-463">Start recording video</span></span>
   * <span data-ttu-id="48af3-464">写真を撮る</span><span class="sxs-lookup"><span data-stu-id="48af3-464">Take a picture</span></span>
   * <span data-ttu-id="48af3-465">ホログラム不透明度を変更します。</span><span class="sxs-lookup"><span data-stu-id="48af3-465">Change hologram opacity</span></span>
   * <span data-ttu-id="48af3-466">(これはキャプチャ カードの待機時間に対応する色のタイムスタンプを調整) フレームのオフセットを変更します。</span><span class="sxs-lookup"><span data-stu-id="48af3-466">Change the frame offset (which adjusts the color timestamp to account for capture card latency)</span></span>
   * <span data-ttu-id="48af3-467">キャプチャに保存するディレクトリを開く</span><span class="sxs-lookup"><span data-stu-id="48af3-467">Open the directory the captures are saved to</span></span>
   * <span data-ttu-id="48af3-468">(プロジェクト内に存在する SpatialMappingManager) 場合は、spectator ビュー カメラから空間マッピング データを要求します。</span><span class="sxs-lookup"><span data-stu-id="48af3-468">Request spatial mapping data from the spectator view camera (if a SpatialMappingManager exists in your project)</span></span>
   * <span data-ttu-id="48af3-469">シーンの複合ビューだけでなく色、ホログラム、およびアルファ チャネルを個別に視覚化します。</span><span class="sxs-lookup"><span data-stu-id="48af3-469">Visualize the scene's composite view as well as color, holograms, and alpha channel individually.</span></span>
   * <span data-ttu-id="48af3-470">カメラの電源をオンにします。</span><span class="sxs-lookup"><span data-stu-id="48af3-470">Turn your camera on.</span></span>
   * <span data-ttu-id="48af3-471">Unity でキーを押して再生します。</span><span class="sxs-lookup"><span data-stu-id="48af3-471">Press play in Unity.</span></span>
   * <span data-ttu-id="48af3-472">カメラを移動すると、Unity でホログラムにフィードのカメラの色の基準とした現実の世界にいる必要があります。</span><span class="sxs-lookup"><span data-stu-id="48af3-472">When the camera is moved, holograms in Unity should be where they are in the real world relative to your camera color feed.</span></span>

## <a name="see-also"></a><span data-ttu-id="48af3-473">関連項目</span><span class="sxs-lookup"><span data-stu-id="48af3-473">See also</span></span>

* [<span data-ttu-id="48af3-474">複合現実のキャプチャ</span><span class="sxs-lookup"><span data-stu-id="48af3-474">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="48af3-475">開発者向けの実際のキャプチャの混在</span><span class="sxs-lookup"><span data-stu-id="48af3-475">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="48af3-476">複合現実での経験を共有</span><span class="sxs-lookup"><span data-stu-id="48af3-476">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* [<span data-ttu-id="48af3-477">Spectator GitHub でコードの表示 (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="48af3-477">Spectator View (Preview) code on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/SpectatorView)
* [<span data-ttu-id="48af3-478">Spectator GitHub でのネイティブ コードの表示 (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="48af3-478">Spectator View (Preview) native code on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)
* [<span data-ttu-id="48af3-479">GitHub で spectator ビュー Pro コード</span><span class="sxs-lookup"><span data-stu-id="48af3-479">Spectator View Pro code on GitHub</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)
