---
title: Unity でのフォーカス ポイント
description: フォーカス ポイントを設定して Unity でホログラム安定性を手動でチューニング
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、フォーカス ポイント、フォーカス平面、安定化平面、安定化のポイント、reprojection、LSR、深度バッファー
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604881"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="5d313-104">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="5d313-104">Focus point in Unity</span></span>

<span data-ttu-id="5d313-105">\**名前空間:\*\*\*UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="5d313-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="5d313-106">**種類**:*HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="5d313-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="5d313-107">[フォーカス ポイント](hologram-stability.md#stabilization-plane)HoloLens、ホログラムを安定化を現在最も実行する方法についてのヒントの指定に設定されている表示できます。</span><span class="sxs-lookup"><span data-stu-id="5d313-107">The [focus point](hologram-stability.md#stabilization-plane) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="5d313-108">Unity でフォーカス ポイントを設定する場合は、すべてのフレームを使用して設定する必要が*HolographicSettings.SetFocusPointForFrame()* します。</span><span class="sxs-lookup"><span data-stu-id="5d313-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="5d313-109">フォーカス ポイントがフレームに設定されていない場合、既定の安定化プレーンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="5d313-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="5d313-110">新しい Unity プロジェクトでは既定では、設定"を有効にする深度バッファーの共有 オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="5d313-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="5d313-111">このオプションでは、没入型のデスクトップ ヘッドセットまたは Windows を実行している HoloLens のいずれかで実行されている Unity アプリ 10 April 2018 Update (RS4) 後では、アプリを指定せず、自動的にホログラム安定性を最適化するために Windows を深度バッファーを送信または、フォーカス ポイント:</span><span class="sxs-lookup"><span data-stu-id="5d313-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="5d313-112">没入型のデスクトップ ヘッドセット、これにはピクセルあたりの深さに基づく reprojection 有効になります。</span><span class="sxs-lookup"><span data-stu-id="5d313-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="5d313-113">Windows を実行している、HoloLens 10 April 2018 Update または後で、分析、最適な安定化平面を自動的に選択する、深度バッファー。</span><span class="sxs-lookup"><span data-stu-id="5d313-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="5d313-114">どちらの方法を提供より高い画質を明示的な作業なしフォーカス ポイントを選択するアプリによって各フレームします。</span><span class="sxs-lookup"><span data-stu-id="5d313-114">Either approach should provide even better image quality without explicit work by your app to select a focus point each frame.</span></span>  <span data-ttu-id="5d313-115">注意くださいフォーカス ポイントを手動で指定する場合と、上記で説明した自動動作をオーバーライド通常ホログラム安定性が削減されます。</span><span class="sxs-lookup"><span data-stu-id="5d313-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="5d313-116">一般に、する必要がありますだけを指定する手動のフォーカス ポイントを Windows に更新されていない HoloLens でアプリが実行されているときに 10 April 2018 Update。</span><span class="sxs-lookup"><span data-stu-id="5d313-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="5d313-117">例</span><span class="sxs-lookup"><span data-stu-id="5d313-117">Example</span></span>

<span data-ttu-id="5d313-118">使用可能なオーバー ロードで推奨されているとおり、フォーカス ポイントを設定する方法はたくさんあります、 *SetFocusPointForFrame*静的関数です。</span><span class="sxs-lookup"><span data-stu-id="5d313-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="5d313-119">次に示す各フレームを指定されたオブジェクトにフォーカス平面を設定する簡単な例を示します。</span><span class="sxs-lookup"><span data-stu-id="5d313-119">Presented below is a simple example to set the focus plane to the provided object each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

<span data-ttu-id="5d313-120">上記の単純なコードがホログラム安定性を減らす場合は、ユーザーの背後にある最終的にフォーカスがあるオブジェクトを終了することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5d313-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="5d313-121">これは、設定「を有効にする深度バッファーの共有」フォーカス ポイントを手動で指定する代わりにためにです。</span><span class="sxs-lookup"><span data-stu-id="5d313-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="5d313-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d313-122">See also</span></span>
* [<span data-ttu-id="5d313-123">安定化プレーン</span><span class="sxs-lookup"><span data-stu-id="5d313-123">Stabilization plane</span></span>](hologram-stability.md#stabilization-plane)
