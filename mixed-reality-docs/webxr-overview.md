---
title: Windows Mixed Reality での WebXR の使用
description: Windows Mixed Reality での WebXR の使用と開発の概要
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR、WinMR、WebAR、WebVR、WindowsMixedReality、HoloLens、windows mixed reality、web vr、web xr、web mr、web ar、360、360 video、360ビデオ、360 photo、360 photos、360コンテンツ、イマーシブ web、immersiveweb、IW
ms.openlocfilehash: 01e6cd44e9879cd7fd9b11e178134eaf364cc53c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278443"
---
# <a name="webxr-overview"></a><span data-ttu-id="73285-104">WebXR の概要</span><span class="sxs-lookup"><span data-stu-id="73285-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="73285-105">WebXR とは</span><span class="sxs-lookup"><span data-stu-id="73285-105">What is WebXR</span></span>

<span data-ttu-id="73285-106">**WebXR DEVICE API**は、 **Web**上の**センサー**や**ヘッドマウントされたディスプレイ**など、**仮想現実 (VR)** デバイスおよび拡張**現実 (AR)** デバイスにアクセスするためのものです。</span><span class="sxs-lookup"><span data-stu-id="73285-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="73285-107">WebXR device API は現在 Microsoft Edge で使用でき、Chrome バージョン79以降では WebXR を既定としてサポートしています。</span><span class="sxs-lookup"><span data-stu-id="73285-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="73285-108">WebXR のブラウザーの最新のサポート状態は、 [caniuse.com](https://caniuse.com/#search=webxr)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="73285-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="73285-109">[Windows Mixed Reality と新しい Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)の詳細については、「新[機能](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="73285-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="73285-110">WebXR の表示</span><span class="sxs-lookup"><span data-stu-id="73285-110">Viewing WebXR</span></span>

<span data-ttu-id="73285-111">ブラウザーが WebXR をサポートしているかどうかをテストするには、ブラウザーで[WebXR サンプル](https://immersive-web.github.io/webxr-samples/)に移動します。</span><span class="sxs-lookup"><span data-stu-id="73285-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="73285-112">参照</span><span class="sxs-lookup"><span data-stu-id="73285-112">See Also</span></span>

* [<span data-ttu-id="73285-113">WebXR Device API 仕様</span><span class="sxs-lookup"><span data-stu-id="73285-113">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="73285-114">WebXR Device API のドキュメント</span><span class="sxs-lookup"><span data-stu-id="73285-114">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="73285-115">Immersiveweb</span><span class="sxs-lookup"><span data-stu-id="73285-115">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="73285-116">WebXR のサンプル</span><span class="sxs-lookup"><span data-stu-id="73285-116">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="73285-117">Windows Mixed Reality と新しい Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="73285-117">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="73285-118">イマーシブ Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="73285-118">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="73285-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="73285-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="73285-120">[ゲームパッド API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)と[ゲームパッド拡張機能](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="73285-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="73285-121">WebGL での失われたコンテキストの処理</span><span class="sxs-lookup"><span data-stu-id="73285-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="73285-122">Pointerlock ロック</span><span class="sxs-lookup"><span data-stu-id="73285-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="73285-123">glTF</span><span class="sxs-lookup"><span data-stu-id="73285-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="73285-124">Babylon を使用して WebXR エクスペリエンスを作成する</span><span class="sxs-lookup"><span data-stu-id="73285-124">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="73285-125">イマーシブ web コミュニティグループ</span><span class="sxs-lookup"><span data-stu-id="73285-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
