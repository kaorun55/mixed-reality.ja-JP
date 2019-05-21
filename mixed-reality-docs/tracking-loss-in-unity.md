---
title: 損失の Unity での追跡
description: 損失の Unity アプリ内の追跡を処理します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、損失の追跡、損失のイメージの追跡
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602771"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="f750c-104">損失の Unity での追跡</span><span class="sxs-lookup"><span data-stu-id="f750c-104">Tracking loss in Unity</span></span>

<span data-ttu-id="f750c-105">デバイスは、世界で自体を見つけられない、アプリで"追跡損失"が発生します。</span><span class="sxs-lookup"><span data-stu-id="f750c-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="f750c-106">既定では、Unity は更新ループを一時停止し、ユーザーにロゴ イメージを表示します。</span><span class="sxs-lookup"><span data-stu-id="f750c-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="f750c-107">追跡を回復すると、ときに、ロゴ イメージは表示されなくなり、update ループが続行されます。</span><span class="sxs-lookup"><span data-stu-id="f750c-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="f750c-108">代わりに、ユーザーはこの遷移を設定を無効にすることによって手動で処理できます。</span><span class="sxs-lookup"><span data-stu-id="f750c-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="f750c-109">すべてのコンテンツは、損失の場合はそれを処理するために何も実行が追跡中にロックされている本文になるようです。</span><span class="sxs-lookup"><span data-stu-id="f750c-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="f750c-110">既定の処理</span><span class="sxs-lookup"><span data-stu-id="f750c-110">Default Handling</span></span>

<span data-ttu-id="f750c-111">既定では、アプリだけでなく、すべてのメッセージおよびイベントの更新ループは損失の追跡の間停止します。</span><span class="sxs-lookup"><span data-stu-id="f750c-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="f750c-112">同時に、ユーザーにイメージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f750c-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="f750c-113">このイメージをカスタマイズするには、編集する]-> [設定]、[Player、ロゴのイメージをクリックし、Holographic 損失の追跡のイメージを設定します。</span><span class="sxs-lookup"><span data-stu-id="f750c-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="f750c-114">手動処理</span><span class="sxs-lookup"><span data-stu-id="f750c-114">Manual Handling</span></span>

<span data-ttu-id="f750c-115">追跡の損失を手動で処理するに移動する必要があります**編集** > **プロジェクト設定** > **Player**  >  **ユニバーサル Windows プラットフォームの設定 タブ** > **スプラッシュ イメージ** > **Windows Holographic** "の追跡が失われる一時停止し、イメージの表示をオフにします。".</span><span class="sxs-lookup"><span data-stu-id="f750c-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="f750c-116">その後、以下で指定した Api を使用した変更の追跡を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f750c-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="f750c-117">**名前空間:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="f750c-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="f750c-118">**種類:** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="f750c-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="f750c-119">追跡の紛失/獲得を検出するためにイベントを公開する世界マネージャー (*WorldManager.OnPositionalLocatorStateChanged*) と現在の状態を照会するプロパティ (*WorldManager.state*)</span><span class="sxs-lookup"><span data-stu-id="f750c-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="f750c-120">追跡の状態がアクティブでない場合、ユーザーに変換しても、仮想世界に変換する、カメラは表示されません。</span><span class="sxs-lookup"><span data-stu-id="f750c-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="f750c-121">つまり、オブジェクトは、物理的な場所に一致しなくなると、ロックされている本文をすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="f750c-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="f750c-122">各フレームまたはハンドルの state プロパティをポーリングする必要がありますか、独自の変更の追跡を処理するときに、 *OnPositionalLocatorStateChanged*イベント。</span><span class="sxs-lookup"><span data-stu-id="f750c-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="f750c-123">ポーリング</span><span class="sxs-lookup"><span data-stu-id="f750c-123">Polling</span></span>

<span data-ttu-id="f750c-124">最も重要な状態が*PositionalLocatorState.Active*追跡は完全に機能することを意味します。</span><span class="sxs-lookup"><span data-stu-id="f750c-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="f750c-125">その他の状態が、メイン カメラに回転差分のみ発生します。</span><span class="sxs-lookup"><span data-stu-id="f750c-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="f750c-126">例:</span><span class="sxs-lookup"><span data-stu-id="f750c-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="f750c-127">OnPositionalLocatorStateChanged イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="f750c-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="f750c-128">サブスクライブできますもまたはしより便利な*OnPositionalLocatorStateChanged*遷移を処理するために。</span><span class="sxs-lookup"><span data-stu-id="f750c-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="f750c-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="f750c-129">See also</span></span>
* [<span data-ttu-id="f750c-130">DirectX が損失する可能性の追跡を処理します。</span><span class="sxs-lookup"><span data-stu-id="f750c-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)
