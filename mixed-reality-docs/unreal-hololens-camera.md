---
title: Unreal での HoloLens 写真/ビデオ カメラ
description: HoloLens 写真/ビデオを Unreal で使用するためのガイド
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, カメラ, PV カメラ, MRC
ms.openlocfilehash: e15ea593283a22dc31cd496de596159035d83799
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720328"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="e089b-104">Unreal での HoloLens 写真/ビデオ カメラ</span><span class="sxs-lookup"><span data-stu-id="e089b-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="e089b-105">概要</span><span class="sxs-lookup"><span data-stu-id="e089b-105">Overview</span></span>

<span data-ttu-id="e089b-106">HoloLens には、Mixed Reality Capture (MRC) に使用される写真/ビデオ (PV) カメラがあり、アプリで実際のビジュアルにアクセスするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="e089b-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="e089b-107">MRC 用の PV カメラからのレンダリング</span><span class="sxs-lookup"><span data-stu-id="e089b-107">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="e089b-108">これには **Unreal Engine 4.25** 以降のバージョンが必要です。</span><span class="sxs-lookup"><span data-stu-id="e089b-108">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="e089b-109">システムとカスタム MRC レコーダーは、PV カメラとイマーシブ アプリによってレンダリングされたホログラムを組み合わせることにより、Mixed Reality キャプチャを作成します。</span><span class="sxs-lookup"><span data-stu-id="e089b-109">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="e089b-110">既定では、Mixed Reality キャプチャでは、右目のホログラフィック出力が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e089b-110">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="e089b-111">イマーシブ アプリが [PV カメラ](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)からのレンダリングを選択した場合は、それが代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="e089b-111">If an immersive app chooses to [render from the PV Camera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="e089b-112">これにより、現実世界と MRC ビデオのホログラムとの間のマッピングが向上します。</span><span class="sxs-lookup"><span data-stu-id="e089b-112">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="e089b-113">PV カメラからの表示をオプトインするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="e089b-113">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="e089b-114">**SetEnabledMixedRealityCamera** および **ResizeMixedRealityCamera** の呼び出し</span><span class="sxs-lookup"><span data-stu-id="e089b-114">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="e089b-115">**サイズ X** および**サイズ Y** の値を使用して、ビデオのディメンションを設定します。</span><span class="sxs-lookup"><span data-stu-id="e089b-115">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![第 3 のカメラ](images/unreal-camera-3rd.PNG)

<span data-ttu-id="e089b-117">その後、Unreal は MRC からのリクエストを処理して、PV カメラの視点からレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="e089b-117">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="e089b-118">[Mixed Reality キャプチャ](mixed-reality-capture.md)がトリガーされた場合にのみ、アプリは写真/ビデオ カメラの視点からレンダリングするよう求められます。</span><span class="sxs-lookup"><span data-stu-id="e089b-118">Only when [Mixed Reality Capture](mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="e089b-119">PV カメラの使用</span><span class="sxs-lookup"><span data-stu-id="e089b-119">Using the PV Camera</span></span>

<span data-ttu-id="e089b-120">Web カメラ テクスチャは実行時にゲームで入手できますが、エディターの **[編集] > [プロジェクトの設定]** で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e089b-120">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="e089b-121">**[プラットフォーム] > [HoloLens] > [機能]** に移動し、**Web カメラ**を確認します。</span><span class="sxs-lookup"><span data-stu-id="e089b-121">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="e089b-122">実行時に Web カメラを使用するには、**StartCameraCapture** 関数を使用し、記録を停止するには、**StopCameraCapture** 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="e089b-122">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![カメラの開始と停止](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="e089b-124">イメージのレンダリング</span><span class="sxs-lookup"><span data-stu-id="e089b-124">Rendering an image</span></span>
<span data-ttu-id="e089b-125">カメラ イメージをレンダリングするには次のようにします。</span><span class="sxs-lookup"><span data-stu-id="e089b-125">To render the camera image:</span></span>
1. <span data-ttu-id="e089b-126">以下のスクリーンショットでは **PVCamMat** という名前のプロジェクトのマテリアルに基づいて、ダイナミック マテリアル インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e089b-126">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="e089b-127">ダイナミック マテリアル インスタンスを **Material Instance Dynamic Object Reference** 変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="e089b-127">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="e089b-128">カメラ フィードをレンダリングするシーン内のオブジェクトのマテリアルを、この新しいダイナミック マテリアル インスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="e089b-128">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="e089b-129">カメラ イメージをマテリアルにバインドするために使用されるタイマーを開始します。</span><span class="sxs-lookup"><span data-stu-id="e089b-129">Start a timer that will be used to bind the camera image to the material.</span></span> 

![カメラのレンダリング](images/unreal-camera-render.PNG)

4. <span data-ttu-id="e089b-131">このタイマーに新しい関数 (この場合は **MaterialTimer**) を作成し、**GetARCameraImage** を呼び出して、Web カメラからテクスチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="e089b-131">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="e089b-132">このテクスチャが有効な場合は、シェーダーのテクスチャ パラメーターをこのイメージに設定します。</span><span class="sxs-lookup"><span data-stu-id="e089b-132">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="e089b-133">そうでない場合は、もう一度素材のタイマーを開始します。</span><span class="sxs-lookup"><span data-stu-id="e089b-133">Otherwise, start the material timer again.</span></span> 

![カメラのテクスチャ](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="e089b-135">マテリアルに、カラー エントリにバインドされている **SetTextureParameterValue** の名前と一致するパラメータがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e089b-135">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="e089b-136">これを行わないと、カメラ イメージを正しく表示できません。</span><span class="sxs-lookup"><span data-stu-id="e089b-136">Without this, the camera image can't be properly displayed.</span></span>

![カメラのテクスチャ](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="e089b-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="e089b-138">See also</span></span>
* [<span data-ttu-id="e089b-139">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="e089b-139">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="e089b-140">開発者向け複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="e089b-140">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
