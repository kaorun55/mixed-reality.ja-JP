---
title: Unity のフォーカスポイント
description: フォーカスポイントを設定して Unity のホログラムの安定性を手動で調整する
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, フォーカスポイント, フォーカスプレーン, 安定化平面, 安定化ポイント, reprojection, LSR, 深度バッファー
ms.openlocfilehash: 9a7f30b552242b24a9a7b260b6574690a27d2c1d
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502623"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="2031b-104">Unity のフォーカスポイント</span><span class="sxs-lookup"><span data-stu-id="2031b-104">Focus point in Unity</span></span>

<span data-ttu-id="2031b-105">**名前空間:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="2031b-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="2031b-106">**型**: *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="2031b-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="2031b-107">[フォーカスポイント](hologram-stability.md#reprojection)は、現在表示されているホログラムに対して安定化を最適に実行する方法について、HoloLens にヒントを提供するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="2031b-107">The [focus point](hologram-stability.md#reprojection) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="2031b-108">Unity でフォーカスポイントを設定する場合は、 *HolographicSettings. SetFocusPointForFrame ()* を使用してすべてのフレームを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2031b-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="2031b-109">フレームにフォーカスポイントが設定されていない場合は、既定の安定化平面が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2031b-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="2031b-110">既定では、新しい Unity プロジェクトの [深度バッファーの共有を有効にする] オプションが設定されています。</span><span class="sxs-lookup"><span data-stu-id="2031b-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="2031b-111">このオプションを使用すると、イマーシブデスクトップヘッドセットまたは Windows 10 April 2018 更新プログラム (RS4) 以降を実行する HoloLens で実行されている Unity アプリは、Windows に深度バッファーを送信して、アプリでを指定することなく、ホログラムの安定性を自動的に最適化します。フォーカスポイント:</span><span class="sxs-lookup"><span data-stu-id="2031b-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="2031b-112">イマーシブデスクトップヘッドセットでは、これにより、ピクセルごとの深度ベースの再プロジェクションが有効になります。</span><span class="sxs-lookup"><span data-stu-id="2031b-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="2031b-113">Windows 10 April 2018 Update 以降を実行している HoloLens では、これにより深度バッファーが分析され、最適な安定化平面が自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="2031b-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="2031b-114">どちらの方法も、各フレームのフォーカスポイントを選択するために、アプリによる明示的な作業を行わずに、より優れたイメージ品質を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2031b-114">Either approach should provide even better image quality without explicit work by your app to select a focus point for each frame.</span></span>  <span data-ttu-id="2031b-115">フォーカスポイントを手動で指定すると、上記の自動動作がオーバーライドされ、通常はホログラムの安定性が低下します。</span><span class="sxs-lookup"><span data-stu-id="2031b-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="2031b-116">一般に、アプリが HoloLens で実行されている場合は、Windows 10 April 2018 更新プログラムにまだ更新されていない場合にのみ、手動のフォーカスポイントを指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2031b-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="2031b-117">例</span><span class="sxs-lookup"><span data-stu-id="2031b-117">Example</span></span>

<span data-ttu-id="2031b-118">*SetFocusPointForFrame*静的関数で使用できるオーバーロードによって提案されているように、フォーカスポイントを設定するにはさまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="2031b-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="2031b-119">次に示すのは、各フレームに対して指定されたオブジェクトにフォーカス平面を設定する簡単な例です。</span><span class="sxs-lookup"><span data-stu-id="2031b-119">Presented below is a simple example to set the focus plane to the provided object for each frame:</span></span>

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

<span data-ttu-id="2031b-120">上の単純なコードでは、フォーカスがあるオブジェクトがユーザーの背後にある場合に、ホログラムの安定性が低下する可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2031b-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="2031b-121">このため、通常は、フォーカスポイントを手動で指定するのではなく、"深度バッファーの共有を有効にする" を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2031b-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="2031b-122">「</span><span class="sxs-lookup"><span data-stu-id="2031b-122">See also</span></span>
* [<span data-ttu-id="2031b-123">安定化平面</span><span class="sxs-lookup"><span data-stu-id="2031b-123">Stabilization plane</span></span>](hologram-stability.md#reprojection)
