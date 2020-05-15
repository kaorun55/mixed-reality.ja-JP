---
title: Unreal での HoloLens カメラ
description: HoloLens カメラを Unreal で使用するためのガイド
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, カメラ, 第 3 のカメラ, MRC
ms.openlocfilehash: 9ef9ce27d161130c6b9f3aa6bb1dbc47d7608ad9
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840121"
---
# <a name="hololens-camera-in-unreal"></a><span data-ttu-id="a7c3a-104">Unreal での HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="a7c3a-104">HoloLens Camera in Unreal</span></span>

## <a name="third-camera-mixed-reality-capture"></a><span data-ttu-id="a7c3a-105">第 3 のカメラの Mixed Reality キャプチャ</span><span class="sxs-lookup"><span data-stu-id="a7c3a-105">Third Camera Mixed Reality Capture</span></span>

<span data-ttu-id="a7c3a-106">第 3 のカメラの Mixed Reality キャプチャ (MRC) を使用すると、目のテクスチャの視点ではなく、HoloLens バイザー上のカメラの視点から Mixed Reality キャプチャをレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-106">Third camera Mixed Reality Capture (MRC) can be used to render a mixed reality capture from the perspective of the camera on the HoloLens visor, rather than the perspective of the eye textures.</span></span>  <span data-ttu-id="a7c3a-107">これにより、現実世界と MRC ビデオのホログラムとの間のマッピングが向上します。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-107">This improves the mapping between the real world and the holograms in the MRC video.</span></span> 

<span data-ttu-id="a7c3a-108">第 3 のカメラの MRC の使用をオプトインするには、SetEnabledMixedRealityCamera と ResizeMixedRealityCamera を必要なビデオの次元で呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-108">To opt into using third camera MRC, call SetEnabledMixedRealityCamera and ResizeMixedRealityCamera with the desired video dimensions.</span></span> 

![第 3 のカメラ](images/unreal-camera-3rd.PNG)

<span data-ttu-id="a7c3a-110">次に、HoloLens デバイス ポータルで MRC ビデオを記録します。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-110">Then record an MRC video in the HoloLens device portal.</span></span> 

## <a name="pv-camera"></a><span data-ttu-id="a7c3a-111">PV カメラ</span><span class="sxs-lookup"><span data-stu-id="a7c3a-111">PV Camera</span></span>

<span data-ttu-id="a7c3a-112">Web カメラのテクスチャを、実行時にゲームで取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-112">The webcam texture can also be retrieved in the game at runtime.</span></span>  <span data-ttu-id="a7c3a-113">HoloLens で Web カメラのテクスチャを実現するには、[プロジェクト設定] > [プラットフォーム] > [HoloLens] > [機能] の下にある Unreal エディターで、最初に "Web カメラ" 機能を確実にオンにします。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-113">To get the webcam texture on HoloLens, first ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> 

<span data-ttu-id="a7c3a-114">StartCameraCapture 関数を使用して、実行時に Web カメラの使用をオプトインします。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-114">Opt into using the webcam at runtime with the StartCameraCapture function.</span></span>  <span data-ttu-id="a7c3a-115">キャプチャを停止するには、StopCameraCapture 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-115">Stop capturing with the StopCameraCapture function.</span></span> 

![カメラの開始と停止](images/unreal-camera-startstop.PNG)

<span data-ttu-id="a7c3a-117">カメラのイメージをレンダリングするには、まず、プロジェクトの素材に基づいて動的な素材のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-117">To render the camera image, first create a dynamic material instance based on a material in the project.</span></span>  <span data-ttu-id="a7c3a-118">この例では、PVCamMat という名前の素材に基づいています。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-118">In this case based on a material named PVCamMat.</span></span>  <span data-ttu-id="a7c3a-119">これを、[Material Instance Dynamic Object Reference]\(素材インスタンスの動的オブジェクト参照\) 型の変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-119">Set this to a variable with type Material Instance Dynamic Object Reference.</span></span>  <span data-ttu-id="a7c3a-120">次に、カメラ フィードをこの新しい動的素材インスタンスにレンダリングするオブジェクトの素材をシーンに設定し、カメラのイメージを素材にバインドするために使用するタイマーを開始します。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-120">Then set the material of the object in the scene that will render the camera feed to this new dynamic material instance and start a timer that will be used to bind the camera image to the material.</span></span> 

![カメラのレンダリング](images/unreal-camera-render.PNG)

<span data-ttu-id="a7c3a-122">このタイマーに新しい関数 (この場合は MaterialTimer) を作成し、GetARCameraImage を呼び出して、Web カメラからテクスチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-122">Create a new function for this timer, in this case MaterialTimer, and call GetARCameraImage to get the texture from the webcam.</span></span>  <span data-ttu-id="a7c3a-123">このテクスチャが有効な場合は、シェーダーのテクスチャ パラメーターをこのイメージに設定します。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-123">If this texture is valid, set a texture parameter in the shader to this image.</span></span>  <span data-ttu-id="a7c3a-124">そうでない場合は、もう一度素材のタイマーを開始します。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-124">Otherwise, start the material timer again.</span></span> 

![カメラのテクスチャ](images/unreal-camera-texture.PNG)

<span data-ttu-id="a7c3a-126">この素材には、カメラのイメージを適切に表示するためにカラー エントリにバインドされている、SetTextureParameterValue 内の名前と一致するパラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="a7c3a-126">The material should have a parameter matching the name in SetTextureParameterValue bound to a color entry to properly display the camera image.</span></span> 

![カメラのテクスチャ](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="a7c3a-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7c3a-128">See also</span></span>
* [<span data-ttu-id="a7c3a-129">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="a7c3a-129">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="a7c3a-130">開発者向け複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="a7c3a-130">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
