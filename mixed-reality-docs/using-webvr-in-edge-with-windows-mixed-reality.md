---
title: Microsoft Edge での WebVR と Windows Mixed Reality の使用
description: Windows Mixed Reality での WebVR の使用と開発の概要
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, web vr, web xr, web mr, web ar, 360, 360 ビデオ, 360 ビデオ, 360 写真, 360 写真, 360 コンテンツ, イマーシブ web, immersiveweb, IW
ms.openlocfilehash: 87805d2c40e9e63cdf3e432189b9deb7d575a380
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437203"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="0e54b-104">Microsoft Edge での WebVR と Windows Mixed Reality の使用</span><span class="sxs-lookup"><span data-stu-id="0e54b-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="0e54b-105">Windows Mixed reality イマーシブヘッドセットの WebVR コンテンツの作成</span><span class="sxs-lookup"><span data-stu-id="0e54b-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="0e54b-106">WebVR 1.1 は、Windows 10 の秋の作成者の更新プログラム以降、Microsoft Edge で利用できます。</span><span class="sxs-lookup"><span data-stu-id="0e54b-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="0e54b-107">開発者は、この API を使用して、web 上でイマーシブ VR エクスペリエンスを作成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="0e54b-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="0e54b-108">WebVR API は、HMD のデータをページに提供します。これを使用すると、ステレオ Webvr シーンを HMD に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="0e54b-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="0e54b-109">API サポートの詳細については、 [Microsoft Edge プラットフォームの状態](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e54b-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="0e54b-110">WebVR API のセキュリティ領域は、Microsoft Edge 内で常に存在します。</span><span class="sxs-lookup"><span data-stu-id="0e54b-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="0e54b-111">ただし、getVRDisplays () を呼び出すと、ヘッドセットが電源に接続されているか、シミュレーターが有効になっている場合にのみ、ヘッドセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="0e54b-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="0e54b-112">Windows Mixed Reality イマーシブヘッドセットの WebVR コンテンツの表示</span><span class="sxs-lookup"><span data-stu-id="0e54b-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="0e54b-113">イマーシブヘッドセットの WebVR コンテンツにアクセスする手順については、「[ユーザーズガイド](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e54b-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="0e54b-114">参照</span><span class="sxs-lookup"><span data-stu-id="0e54b-114">See Also</span></span>
* [<span data-ttu-id="0e54b-115">WebVR 情報</span><span class="sxs-lookup"><span data-stu-id="0e54b-115">WebVR information</span></span>](https://webvr.info)
* [<span data-ttu-id="0e54b-116">WebVR 仕様</span><span class="sxs-lookup"><span data-stu-id="0e54b-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="0e54b-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="0e54b-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="0e54b-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="0e54b-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="0e54b-119">[ゲームパッド API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)と[ゲームパッド拡張機能](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="0e54b-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="0e54b-120">WebGL での失われたコンテキストの処理</span><span class="sxs-lookup"><span data-stu-id="0e54b-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="0e54b-121">Pointerlock ロック</span><span class="sxs-lookup"><span data-stu-id="0e54b-121">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="0e54b-122">glTF</span><span class="sxs-lookup"><span data-stu-id="0e54b-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="0e54b-123">Babylon を使用して WebVR を有効にする</span><span class="sxs-lookup"><span data-stu-id="0e54b-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

