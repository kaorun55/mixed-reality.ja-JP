---
title: Windows Mixed Reality を新しい Unity プロジェクトを構成します。
description: MRTK なしの Unity プロジェクトを構成します。
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity では、実際には、開発、はじめに、新しいプロジェクトの混在
ms.openlocfilehash: aad38474781fd78425d48034877122d36d9e3e93
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65940753"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="e17e1-104">Windows Mixed Reality を新しい Unity プロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="e17e1-104">Configure a New Unity Project for Windows Mixed Reality</span></span> 

<span data-ttu-id="e17e1-105">(MRTK v2 は、Unity プロジェクトに既にインポートした場合は省略)</span><span class="sxs-lookup"><span data-stu-id="e17e1-105">(skip if you have already imported MRTK v2 into your Unity Project)</span></span>

<span data-ttu-id="e17e1-106">Mixed Reality ツールキットをインポートせず、新しい Unity プロジェクトを作成したい場合は、少数の Unity の設定が 2 つのカテゴリに分類、Windows Mixed Reality を手動で変更する必要があります。 プロジェクトごとおよびシーンごと。</span><span class="sxs-lookup"><span data-stu-id="e17e1-106">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality, broken down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="e17e1-107">プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="e17e1-107">Per-project settings</span></span>

<span data-ttu-id="e17e1-108">Windows Mixed Reality を対象とは、まず、ユニバーサル Windows プラットフォーム アプリとしてエクスポートする Unity プロジェクトを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e17e1-108">To target Windows Mixed Reality, you first need to set your Unity project to export as a Universal Windows Platform app:</span></span>
1. <span data-ttu-id="e17e1-109">選択**ファイル > の設定を作成しています.**</span><span class="sxs-lookup"><span data-stu-id="e17e1-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="e17e1-110">選択**ユニバーサル Windows プラットフォーム**、プラットフォームに一覧表示し、クリックして**スイッチ プラットフォーム**</span><span class="sxs-lookup"><span data-stu-id="e17e1-110">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="e17e1-111">設定**SDK**に**ユニバーサル 10**</span><span class="sxs-lookup"><span data-stu-id="e17e1-111">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="e17e1-112">設定**ターゲット デバイス**に**任意のデバイス**イマーシブ ヘッドセットをサポートするかに切り替えてに**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="e17e1-112">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="e17e1-113">設定**ビルドの種類**に**D3D**</span><span class="sxs-lookup"><span data-stu-id="e17e1-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="e17e1-114">設定**UWP SDK**に**インストールされている最新**</span><span class="sxs-lookup"><span data-stu-id="e17e1-114">Set **UWP SDK** to **Latest installed**</span></span>

<span data-ttu-id="e17e1-115">Unity エクスポートしようとしましたが、アプリが作成することを把握できるようにする必要があります、[没入型ビュー](app-views.md) 2D ビューではなく。</span><span class="sxs-lookup"><span data-stu-id="e17e1-115">We then need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="e17e1-116">そのために、「仮想現実サポート」を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e17e1-116">We do that by enabling "Virtual Reality Supported":</span></span>
1. <span data-ttu-id="e17e1-117">**ビルド設定しています.** ウィンドウを開いて、**プレーヤー設定しています.**</span><span class="sxs-lookup"><span data-stu-id="e17e1-117">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="e17e1-118">選択、**ユニバーサル Windows プラットフォームの設定** タブ</span><span class="sxs-lookup"><span data-stu-id="e17e1-118">Select the **Settings for Universal Windows Platform** tab</span></span>
3. <span data-ttu-id="e17e1-119">展開、 **XR 設定**グループ</span><span class="sxs-lookup"><span data-stu-id="e17e1-119">Expand the **XR Settings** group</span></span>
4. <span data-ttu-id="e17e1-120">**XR 設定** セクションで、チェック、**仮想現実サポート**を追加するチェック ボックスをオン、**仮想現実デバイス**一覧。</span><span class="sxs-lookup"><span data-stu-id="e17e1-120">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
5. <span data-ttu-id="e17e1-121">**XR 設定**グループで、ことを確認します **"Windows Mixed Reality"** サポートされているデバイスとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="e17e1-121">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="e17e1-122">(この場合がありますに表示されます"Windows Holographic"として以前のバージョンの Unity)</span><span class="sxs-lookup"><span data-stu-id="e17e1-122">(this may appear as "Windows Holographic" in older versions of Unity)</span></span>

<span data-ttu-id="e17e1-123">![Unity の品質の設定](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="e17e1-123">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="e17e1-124">*Unity xr の設定*</span><span class="sxs-lookup"><span data-stu-id="e17e1-124">*Unity xr settings*</span></span>

<span data-ttu-id="e17e1-125">アプリは、基本的な holographic レンダリングと空間の入力を今すぐ実行できます。</span><span class="sxs-lookup"><span data-stu-id="e17e1-125">Your app can now do basic holographic rendering and spatial input.</span></span> <span data-ttu-id="e17e1-126">さらに移動し、特定の機能を活用するには、アプリは、自らのマニフェストで適切な機能を宣言しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="e17e1-126">To go further and take advantage of certain functionality, your app must declare the appropriate capabilities in its manifest.</span></span> <span data-ttu-id="e17e1-127">すべての後続のプロジェクトのエクスポートに含まれるように、Unity でマニフェストの宣言を作成できます。</span><span class="sxs-lookup"><span data-stu-id="e17e1-127">The manifest declarations can be made in Unity so they are included in every subsequent project export.</span></span> <span data-ttu-id="e17e1-128">設定がある**プレーヤー設定 > ユニバーサル Windows プラットフォームの設定 > 発行の設定 > 機能**します。</span><span class="sxs-lookup"><span data-stu-id="e17e1-128">The setting are found in **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> <span data-ttu-id="e17e1-129">For Mixed Reality Unity Api の一般的な使用を有効にするための適用可能な機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e17e1-129">The applicable capabilities for enabling commonly-used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="e17e1-130">機能</span><span class="sxs-lookup"><span data-stu-id="e17e1-130">Capability</span></span>  |  <span data-ttu-id="e17e1-131">Api の機能を必要とします。</span><span class="sxs-lookup"><span data-stu-id="e17e1-131">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="e17e1-132">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="e17e1-132">SpatialPerception</span></span>  |  <span data-ttu-id="e17e1-133">SurfaceObserver (へのアクセスを[空間マッピング](spatial-mapping.md)HoloLens でメッシュ)&mdash;*ヘッドセットの一般的な空間の追跡に必要な機能もありません*</span><span class="sxs-lookup"><span data-stu-id="e17e1-133">SurfaceObserver (access to [spatial mapping](spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="e17e1-134">WebCam</span><span class="sxs-lookup"><span data-stu-id="e17e1-134">WebCam</span></span>  |  <span data-ttu-id="e17e1-135">PhotoCapture と VideoCapture</span><span class="sxs-lookup"><span data-stu-id="e17e1-135">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="e17e1-136">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="e17e1-136">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="e17e1-137">PhotoCapture または VideoCapture、それぞれ (格納するときにキャプチャしたコンテンツ)</span><span class="sxs-lookup"><span data-stu-id="e17e1-137">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="e17e1-138">マイク</span><span class="sxs-lookup"><span data-stu-id="e17e1-138">Microphone</span></span>  |  <span data-ttu-id="e17e1-139">VideoCapture (オーディオをキャプチャ) するときに、DictationRecognizer、GrammarRecognizer、および KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="e17e1-139">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="e17e1-140">internetClient</span><span class="sxs-lookup"><span data-stu-id="e17e1-140">InternetClient</span></span>  |  <span data-ttu-id="e17e1-141">DictationRecognizer (および Unity Profiler を使用する)</span><span class="sxs-lookup"><span data-stu-id="e17e1-141">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

<span data-ttu-id="e17e1-142">**Unity の品質の設定**</span><span class="sxs-lookup"><span data-stu-id="e17e1-142">**Unity quality settings**</span></span>

<span data-ttu-id="e17e1-143">![Unity の品質の設定](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="e17e1-143">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="e17e1-144">*Unity の品質の設定*</span><span class="sxs-lookup"><span data-stu-id="e17e1-144">*Unity quality settings*</span></span>

<span data-ttu-id="e17e1-145">HoloLens では、mobile クラス GPU があります。</span><span class="sxs-lookup"><span data-stu-id="e17e1-145">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="e17e1-146">場合は、アプリは、HoloLens をターゲットとするが、完全なフレーム レートを維持するということを確認する最速のパフォーマンス チューニング、品質設定します。</span><span class="sxs-lookup"><span data-stu-id="e17e1-146">If your app is targeting HoloLens, you'll want the quality settings tuned for fastest performance to ensure we maintain full framerate:</span></span>
1. <span data-ttu-id="e17e1-147">選択**編集 > プロジェクトの設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="e17e1-147">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="e17e1-148">選択、**ドロップダウン**下、 **Windows ストア**ロゴと選択**Very Low**します。</span><span class="sxs-lookup"><span data-stu-id="e17e1-148">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="e17e1-149">設定すると正しく適用はご存知でしょう Windows ストアの列にあるボックスと**Very Low**行は緑色です。</span><span class="sxs-lookup"><span data-stu-id="e17e1-149">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="e17e1-150">シーンごとの設定</span><span class="sxs-lookup"><span data-stu-id="e17e1-150">Per-scene settings</span></span>

<span data-ttu-id="e17e1-151">**Unity のカメラ設定**</span><span class="sxs-lookup"><span data-stu-id="e17e1-151">**Unity camera settings**</span></span>

<span data-ttu-id="e17e1-152">![Unity のカメラ設定](images/Unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="e17e1-152">![Unity camera settings](images/Unitycamerasettings.png)</span></span><br>
<span data-ttu-id="e17e1-153">*Unity のカメラ設定*</span><span class="sxs-lookup"><span data-stu-id="e17e1-153">*Unity camera settings*</span></span>

<span data-ttu-id="e17e1-154">「仮想現実サポート」チェック ボックスを有効にすると、 [Unity カメラ](camera-in-unity.md)コンポーネント ハンドル[追跡とステレオスコ ピック レンダリング ヘッド](rendering.md)します。</span><span class="sxs-lookup"><span data-stu-id="e17e1-154">Once you enable the "Virtual Reality Supported" checkbox, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](rendering.md).</span></span> <span data-ttu-id="e17e1-155">これを行うカスタム カメラに置き換える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e17e1-155">There is no need to replace it with a custom camera to do this.</span></span>

<span data-ttu-id="e17e1-156">アプリでは、具体的には HoloLens をターゲットが場合、は、現実の世界をアプリに表示されますので、デバイスの透過的な表示、最適化するために変更する必要があるいくつかの設定があります。</span><span class="sxs-lookup"><span data-stu-id="e17e1-156">If your app is targeting HoloLens specifically, there are a few settings that need to be changed to optimize for the device's transparent displays, so your app will show through to the physical world:</span></span>
1. <span data-ttu-id="e17e1-157">**階層**を選択、 **Main Camera**</span><span class="sxs-lookup"><span data-stu-id="e17e1-157">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="e17e1-158">**インスペクター**パネルで、設定、変換**位置**に**0, 0, 0**ユーザー ヘッドの位置が、Unity の世界配信元で起動するようです。</span><span class="sxs-lookup"><span data-stu-id="e17e1-158">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the users head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="e17e1-159">変更**フラグをクリア**に**単色**します。</span><span class="sxs-lookup"><span data-stu-id="e17e1-159">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="e17e1-160">変更、**バック グラウンド**する色**RGBA 0,0,0,0**します。</span><span class="sxs-lookup"><span data-stu-id="e17e1-160">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="e17e1-161">黒は、HoloLens で透明としてレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="e17e1-161">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="e17e1-162">変更**Clipping - つまり近く**を[推奨 HoloLens](camera-in-unity.md#clip-planes) 0.85 (メートル)。</span><span class="sxs-lookup"><span data-stu-id="e17e1-162">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="e17e1-163">削除し、新しいカメラを作成した場合、カメラが確認**タグ**として**MainCamera**します。</span><span class="sxs-lookup"><span data-stu-id="e17e1-163">If you delete and create a new camera, make sure your camera is **Tagged** as **MainCamera**.</span></span>


## <a name="see-also"></a><span data-ttu-id="e17e1-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="e17e1-164">See also</span></span>
* [<span data-ttu-id="e17e1-165">複合現実 Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="e17e1-165">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="e17e1-166">Unity 開発の概要</span><span class="sxs-lookup"><span data-stu-id="e17e1-166">Unity Development Overview</span></span>](unity-development-overview.md)
