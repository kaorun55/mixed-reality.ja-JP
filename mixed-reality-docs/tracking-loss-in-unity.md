---
title: Unity での損失の追跡
description: Unity アプリ内での追跡損失の処理。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、損失の追跡、損失の追跡の画像
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548745"
---
# <a name="tracking-loss-in-unity"></a>Unity での損失の追跡

デバイスが世界中で見つからない場合、アプリでは "損失の追跡" が発生します。 既定では、Unity は update ループを一時停止し、ユーザーにスプラッシュイメージを表示します。 追跡が再開されると、スプラッシュイメージが消え、update ループが続行します。

別の方法として、ユーザーは設定から除外することによって、この移行を手動で処理できます。 コンテンツを処理する処理が何も行われていない場合、追跡が失われても、すべてのコンテンツが本文でロックされているように見えます。

## <a name="default-handling"></a>既定の処理

既定では、アプリの更新ループとすべてのメッセージとイベントは、追跡が失われている間停止します。 同時に、画像がユーザーに表示されます。 このイメージをカスタマイズするには、[編集-> 設定-> プレーヤー] に移動し、[スプラッシュイメージ] をクリックして、Holographic Tracking ロスイメージを設定します。

## <a name="manual-handling"></a>手動処理

追跡の損失を手動で処理するには、 > [**プロジェクト設定** > の**編集** > ]、[**設定] タブ** > の **[スプラッシュ画像]** のユニバーサルWindowsプラットフォームに進む必要があります。 > **Windows Holographic**をオフにして、[トラックの損失を一時停止し、画像を表示する] をオフにします。 その後、以下で指定した Api を使用して、変更の追跡を処理する必要があります。

**名前空間:**  *UnityEngine.XR.WSA*<br>
**種類:** *WorldManager*

* World Manager は、紛失/獲得された追跡 (*WorldManager OnPositionalLocatorStateChanged*) を検出するイベントを公開し、プロパティを表示して現在の状態 (WorldManager) を照会し*ます。*
* 追跡状態がアクティブでない場合、カメラは、ユーザーが変換した場合でも、仮想環境では変換されないように見えます。 これは、オブジェクトが物理的な場所に対応しなくなり、すべての本文がロックされることを意味します。

変更の追跡を自分で処理する場合は、各フレームの状態プロパティをポーリングするか、 *OnPositionalLocatorStateChanged*イベントを処理する必要があります。

### <a name="polling"></a>ポーリング

最も重要な状態は*Positionallocatorstate です。アクティブ*とは、追跡が完全に機能していることを意味します。 その他の状態では、メインカメラへの回転デルタのみが発生します。 以下に例を示します。

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>OnPositionalLocatorStateChanged イベントの処理

また、 *OnPositionalLocatorStateChanged*にサブスクライブして遷移を処理することもできます。

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

## <a name="see-also"></a>関連項目
* [DirectX での追跡損失の処理](coordinate-systems-in-directx.md#handling-tracking-loss)
