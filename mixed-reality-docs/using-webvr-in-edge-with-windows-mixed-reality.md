---
title: Windows Mixed Reality WebVR を Microsoft Edge でを使用しました。
description: 使用して、Windows Mixed Reality で WebVR 用の開発の概要
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR、WebXR、WinMR、WebAR、vr を web、web xr、mr を web、web ar、360、360 のビデオ、360 ビデオ、360 の写真、360 の写真、360 コンテンツ、没入型の web、immersiveweb、インフォメーション ワーカー
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604638"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="7f7ff-104">Windows Mixed Reality WebVR を Microsoft Edge でを使用しました。</span><span class="sxs-lookup"><span data-stu-id="7f7ff-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="7f7ff-105">Windows Mixed reality を WebVR コンテンツ イマーシブ ヘッドセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="7f7ff-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="7f7ff-106">WebVR 1.1 は Windows 10 Fall Creators Update 以降の Microsoft Edge で使用できます。</span><span class="sxs-lookup"><span data-stu-id="7f7ff-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="7f7ff-107">今すぐ開発者は、この API を使用して、web で没入型の VR エクスペリエンスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="7f7ff-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="7f7ff-108">WebVR API では、ッドマウントにステレオ WebGL シーンをレンダリングするために使用できるページにッドマウント姿勢のデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="7f7ff-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="7f7ff-109">API のサポートの詳細についてで使用できる、 [Microsoft Edge プラットフォームの状態ページ](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/)します。</span><span class="sxs-lookup"><span data-stu-id="7f7ff-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="7f7ff-110">WebVR API サーフェス領域は、Microsoft Edge 内で常に存在します。</span><span class="sxs-lookup"><span data-stu-id="7f7ff-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="7f7ff-111">ただし、シミュレーターがオンにされましたかヘッドセット接続されている場合、getVRDisplays() への呼び出しはヘッドセットを返すのみです。</span><span class="sxs-lookup"><span data-stu-id="7f7ff-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="7f7ff-112">Windows Mixed Reality イマーシブ ヘッドセットで WebVR コンテンツを表示</span><span class="sxs-lookup"><span data-stu-id="7f7ff-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="7f7ff-113">イマーシブ ヘッドセット WebVR コンテンツにアクセスするための手順が記載されて、[愛好家のガイド](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)します。</span><span class="sxs-lookup"><span data-stu-id="7f7ff-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f7ff-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f7ff-114">See Also</span></span>
* [<span data-ttu-id="7f7ff-115">WebVR 情報</span><span class="sxs-lookup"><span data-stu-id="7f7ff-115">WebVR information</span></span>](http://webvr.info)
* [<span data-ttu-id="7f7ff-116">WebVR 仕様</span><span class="sxs-lookup"><span data-stu-id="7f7ff-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="7f7ff-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="7f7ff-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="7f7ff-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="7f7ff-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="7f7ff-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)と[ゲームパッドの拡張機能](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="7f7ff-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="7f7ff-120">WebGL でコンテキストが失われる処理</span><span class="sxs-lookup"><span data-stu-id="7f7ff-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="7f7ff-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="7f7ff-121">Pointerlock</span></span>](http://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="7f7ff-122">glTF</span><span class="sxs-lookup"><span data-stu-id="7f7ff-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="7f7ff-123">Babylon.js を使用して WebVR を有効にするには</span><span class="sxs-lookup"><span data-stu-id="7f7ff-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

