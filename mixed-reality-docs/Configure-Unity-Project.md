---
title: Windows Mixed Reality 用の新しい Unity プロジェクトを構成する
description: MRTK を使用せずに Unity プロジェクトを構成する
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, mixed reality, 開発, 作業の開始, 新しいプロジェクト
ms.openlocfilehash: 99c72f2d9d900c8a05fb7d8b9b8de10d657fdd13
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502653"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="fca3a-104">Windows Mixed Reality 用の新しい Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="fca3a-104">Configure a New Unity Project for Windows Mixed Reality</span></span> 

<span data-ttu-id="fca3a-105">(Unity プロジェクトに MRTK v2 が既にインポートされている場合はスキップします)</span><span class="sxs-lookup"><span data-stu-id="fca3a-105">(skip if you have already imported MRTK v2 into your Unity Project)</span></span>

<span data-ttu-id="fca3a-106">混合 Reality ツールキットをインポートせずに新しい Unity プロジェクトを作成する場合は、Windows Mixed Reality に対して手動で変更する必要がある Unity 設定の小さなセットがあります。これは、プロジェクトごととシーン単位の2つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="fca3a-106">If you'd like to create a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality, broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="fca3a-107">プロジェクトごとの設定</span><span class="sxs-lookup"><span data-stu-id="fca3a-107">Per-project settings</span></span>

<span data-ttu-id="fca3a-108">Windows Mixed Reality をターゲットにするには、最初に Unity プロジェクトをユニバーサル Windows プラットフォームアプリとしてエクスポートするように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fca3a-108">To target Windows Mixed Reality, you first need to set your Unity project to export as a Universal Windows Platform app:</span></span> 
1. <span data-ttu-id="fca3a-109">**ファイル > ビルド設定**を選択してください...</span><span class="sxs-lookup"><span data-stu-id="fca3a-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="fca3a-110">プラットフォーム ボックスの一覧の **ユニバーサル Windows プラットフォーム**を選択し、**プラットフォームの切り替え** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fca3a-110">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="fca3a-111">**SDK**を**Universal 10**に設定する</span><span class="sxs-lookup"><span data-stu-id="fca3a-111">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="fca3a-112">イマーシブヘッドセットまたは**HoloLens**への切り替えをサポートするために、**ターゲットデバイス**を**任意のデバイス**に設定する</span><span class="sxs-lookup"><span data-stu-id="fca3a-112">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="fca3a-113">**ビルドの種類**を**D3D**に設定</span><span class="sxs-lookup"><span data-stu-id="fca3a-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="fca3a-114">**UWP SDK**を**最新のインストール**に設定する</span><span class="sxs-lookup"><span data-stu-id="fca3a-114">Set **UWP SDK** to **Latest installed**</span></span>

<span data-ttu-id="fca3a-115">次に、エクスポートしようとしているアプリが2D ビューではなく[イマーシブビュー](app-views.md)を作成する必要があることを Unity に知らせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="fca3a-115">You then need to let Unity know that the app you are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="fca3a-116">これを行うには、"Virtual Reality がサポートされている" を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fca3a-116">You do that by enabling "Virtual Reality Supported":</span></span>
1. <span data-ttu-id="fca3a-117">**[ビルドの設定...]** ウィンドウで、プレーヤーの **[設定]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="fca3a-117">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="fca3a-118">[ユニバーサル Windows プラットフォーム] タブ**の設定**を選択します。</span><span class="sxs-lookup"><span data-stu-id="fca3a-118">Select the **Settings for Universal Windows Platform** tab</span></span>
3. <span data-ttu-id="fca3a-119">**[XR Settings]** グループを展開します。</span><span class="sxs-lookup"><span data-stu-id="fca3a-119">Expand the **XR Settings** group</span></span>
4. <span data-ttu-id="fca3a-120">**[XR の設定]** セクションで、 **[仮想現実のサポート]** チェックボックスをオンにして、 **[仮想現実のデバイス]** の一覧を追加します。</span><span class="sxs-lookup"><span data-stu-id="fca3a-120">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
5. <span data-ttu-id="fca3a-121">**[XR 設定]** グループで、 **"Windows Mixed Reality"** がサポートされているデバイスとして表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fca3a-121">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="fca3a-122">(以前のバージョンの Unity では、"Windows Holographic" として表示される場合があります)</span><span class="sxs-lookup"><span data-stu-id="fca3a-122">(this may appear as "Windows Holographic" in older versions of Unity)</span></span>

<span data-ttu-id="fca3a-123">![Unity 品質設定](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="fca3a-123">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="fca3a-124">*Unity xr の設定*</span><span class="sxs-lookup"><span data-stu-id="fca3a-124">*Unity xr settings*</span></span>

<span data-ttu-id="fca3a-125">これで、アプリで基本的な holographic のレンダリングと空間入力を行うことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="fca3a-125">Your app can now do basic holographic rendering and spatial input.</span></span> <span data-ttu-id="fca3a-126">特定の機能を利用するには、アプリでマニフェスト内の適切な機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fca3a-126">To go further and take advantage of certain functionality, your app must declare the appropriate capabilities in its manifest.</span></span> <span data-ttu-id="fca3a-127">マニフェスト宣言は Unity で作成できるため、後続のすべてのプロジェクトエクスポートに含まれます。</span><span class="sxs-lookup"><span data-stu-id="fca3a-127">The manifest declarations can be made in Unity so they are included in every subsequent project export.</span></span> <span data-ttu-id="fca3a-128">設定は、**ユニバーサル Windows プラットフォーム > の発行設定 > 機能の [プレーヤーの設定 > 設定**] にあります。</span><span class="sxs-lookup"><span data-stu-id="fca3a-128">The settings are found in **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> <span data-ttu-id="fca3a-129">一般的に使用される Unity Api を混合現実に対して有効にするための適用可能な機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fca3a-129">The applicable capabilities for enabling commonly-used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="fca3a-130">機能</span><span class="sxs-lookup"><span data-stu-id="fca3a-130">Capability</span></span>  |  <span data-ttu-id="fca3a-131">機能を必要とする Api</span><span class="sxs-lookup"><span data-stu-id="fca3a-131">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="fca3a-132">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="fca3a-132">SpatialPerception</span></span>  |  <span data-ttu-id="fca3a-133">SurfaceObserver (HoloLens の[空間マッピング](spatial-mapping.md)メッシュへのアクセス)&mdash;*ヘッドセットの一般的な空間追跡に必要な機能はありません*</span><span class="sxs-lookup"><span data-stu-id="fca3a-133">SurfaceObserver (access to [spatial mapping](spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="fca3a-134">WebCam</span><span class="sxs-lookup"><span data-stu-id="fca3a-134">WebCam</span></span>  |  <span data-ttu-id="fca3a-135">PhotoCapture と VideoCapture</span><span class="sxs-lookup"><span data-stu-id="fca3a-135">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="fca3a-136">PicturesLibrary / VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="fca3a-136">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="fca3a-137">PhotoCapture または VideoCapture (キャプチャされたコンテンツを格納する場合)</span><span class="sxs-lookup"><span data-stu-id="fca3a-137">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="fca3a-138">マイク</span><span class="sxs-lookup"><span data-stu-id="fca3a-138">Microphone</span></span>  |  <span data-ttu-id="fca3a-139">VideoCapture (オーディオをキャプチャする場合)、DictationRecognizer、GrammarRecognizer、および KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="fca3a-139">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="fca3a-140">InternetClient</span><span class="sxs-lookup"><span data-stu-id="fca3a-140">InternetClient</span></span>  |  <span data-ttu-id="fca3a-141">DictationRecognizer (および Unity Profiler の使用)</span><span class="sxs-lookup"><span data-stu-id="fca3a-141">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

<span data-ttu-id="fca3a-142">**Unity の品質設定**</span><span class="sxs-lookup"><span data-stu-id="fca3a-142">**Unity quality settings**</span></span>

<span data-ttu-id="fca3a-143">![Unity 品質設定](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="fca3a-143">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="fca3a-144">*Unity の品質設定*</span><span class="sxs-lookup"><span data-stu-id="fca3a-144">*Unity quality settings*</span></span>

<span data-ttu-id="fca3a-145">HoloLens には、モバイルクラスの GPU があります。</span><span class="sxs-lookup"><span data-stu-id="fca3a-145">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="fca3a-146">アプリが HoloLens を対象としている場合は、完全なフレームレートを維持するために、品質設定のパフォーマンスを最速に調整することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fca3a-146">If your app is targeting HoloLens, you'll want the quality settings tuned for fastest performance to ensure we maintain full framerate:</span></span>
1. <span data-ttu-id="fca3a-147">**[プロジェクト設定の編集 > の > 品質]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fca3a-147">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="fca3a-148">**Windows ストア**のロゴの下にある**ドロップダウン**を選択し、 **[非常に低い]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fca3a-148">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="fca3a-149">Windows ストアの列のボックスと**非常に少ない**行が緑色になっている場合は、設定が正しく適用されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="fca3a-149">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="fca3a-150">シーンごとの設定</span><span class="sxs-lookup"><span data-stu-id="fca3a-150">Per-scene settings</span></span>

<span data-ttu-id="fca3a-151">**Unity カメラの設定**</span><span class="sxs-lookup"><span data-stu-id="fca3a-151">**Unity camera settings**</span></span>

<span data-ttu-id="fca3a-152">![Unity カメラの設定](images/Unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="fca3a-152">![Unity camera settings](images/Unitycamerasettings.png)</span></span><br>
<span data-ttu-id="fca3a-153">*Unity カメラの設定*</span><span class="sxs-lookup"><span data-stu-id="fca3a-153">*Unity camera settings*</span></span>

<span data-ttu-id="fca3a-154">"Virtual Reality がサポートされています" チェックボックスをオンにすると、 [Unity カメラ](camera-in-unity.md)コンポーネントは[ヘッドトラッキングとステレオスコピックレンダリング](rendering.md)を処理します。</span><span class="sxs-lookup"><span data-stu-id="fca3a-154">Once you enable the "Virtual Reality Supported" checkbox, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](rendering.md).</span></span> <span data-ttu-id="fca3a-155">これを行うには、カスタムカメラで置き換える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fca3a-155">There is no need to replace it with a custom camera to do this.</span></span>

<span data-ttu-id="fca3a-156">アプリが HoloLens を対象としている場合は、デバイスの透明なディスプレイを最適化するために変更する必要がある設定がいくつかあります。そのため、アプリは物理的な世界に表示されます。</span><span class="sxs-lookup"><span data-stu-id="fca3a-156">If your app is targeting HoloLens specifically, there are a few settings that need to be changed to optimize for the device's transparent displays, so your app will show through to the physical world:</span></span>
1. <span data-ttu-id="fca3a-157">**階層**で、**メインカメラ**を選択します。</span><span class="sxs-lookup"><span data-stu-id="fca3a-157">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="fca3a-158">**[インスペクター]** パネルで、変換 **[位置]** を**0、0、0**に設定します。これにより、ユーザーのヘッドの位置が Unity の元の場所から開始されます。</span><span class="sxs-lookup"><span data-stu-id="fca3a-158">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="fca3a-159">**クリアフラグ**を**純色**に変更します。</span><span class="sxs-lookup"><span data-stu-id="fca3a-159">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="fca3a-160">**背景**色を**RGBA 0、0、0、0**に変更します。</span><span class="sxs-lookup"><span data-stu-id="fca3a-160">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="fca3a-161">ブラックは HoloLens では透明としてレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="fca3a-161">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="fca3a-162">**クリッププレーン**を[HoloLens の推奨](camera-in-unity.md#clip-planes)0.85 (メーター) に近い場所に変更します。</span><span class="sxs-lookup"><span data-stu-id="fca3a-162">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="fca3a-163">新しいカメラを削除して作成する場合は、カメラが**maincamera**として**タグ付け**されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fca3a-163">If you delete and create a new camera, make sure your camera is **Tagged** as **MainCamera**.</span></span>


## <a name="see-also"></a><span data-ttu-id="fca3a-164">「</span><span class="sxs-lookup"><span data-stu-id="fca3a-164">See also</span></span>
* [<span data-ttu-id="fca3a-165">Mixed Reality Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="fca3a-165">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="fca3a-166">Unity 開発の概要</span><span class="sxs-lookup"><span data-stu-id="fca3a-166">Unity Development Overview</span></span>](unity-development-overview.md)
