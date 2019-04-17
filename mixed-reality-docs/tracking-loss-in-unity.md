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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602771"
---
# <a name="tracking-loss-in-unity"></a>損失の Unity での追跡

デバイスは、世界で自体を見つけられない、アプリで"追跡損失"が発生します。 既定では、Unity は更新ループを一時停止し、ユーザーにロゴ イメージを表示します。 追跡を回復すると、ときに、ロゴ イメージは表示されなくなり、update ループが続行されます。

代わりに、ユーザーはこの遷移を設定を無効にすることによって手動で処理できます。 すべてのコンテンツは、損失の場合はそれを処理するために何も実行が追跡中にロックされている本文になるようです。

## <a name="default-handling"></a>既定の処理

既定では、アプリだけでなく、すべてのメッセージおよびイベントの更新ループは損失の追跡の間停止します。 同時に、ユーザーにイメージが表示されます。 このイメージをカスタマイズするには、編集する]-> [設定]、[Player、ロゴのイメージをクリックし、Holographic 損失の追跡のイメージを設定します。

## <a name="manual-handling"></a>手動処理

追跡の損失を手動で処理するに移動する必要があります**編集** > **プロジェクト設定** > **Player**  >  **ユニバーサル Windows プラットフォームの設定 タブ** > **スプラッシュ イメージ** > **Windows Holographic** "の追跡が失われる一時停止し、イメージの表示をオフにします。". その後、以下で指定した Api を使用した変更の追跡を処理する必要があります。

**名前空間:***UnityEngine.XR.WSA*<br>
**種類:***WorldManager*

* 追跡の紛失/獲得を検出するためにイベントを公開する世界マネージャー (*WorldManager.OnPositionalLocatorStateChanged*) と現在の状態を照会するプロパティ (*WorldManager.state*)
* 追跡の状態がアクティブでない場合、ユーザーに変換しても、仮想世界に変換する、カメラは表示されません。 つまり、オブジェクトは、物理的な場所に一致しなくなると、ロックされている本文をすべて表示されます。

各フレームまたはハンドルの state プロパティをポーリングする必要がありますか、独自の変更の追跡を処理するときに、 *OnPositionalLocatorStateChanged*イベント。

### <a name="polling"></a>ポーリング

最も重要な状態が*PositionalLocatorState.Active*追跡は完全に機能することを意味します。 その他の状態が、メイン カメラに回転差分のみ発生します。 例:

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>OnPositionalLocatorStateChanged イベントを処理します。

サブスクライブできますもまたはしより便利な*OnPositionalLocatorStateChanged*遷移を処理するために。

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
* [DirectX が損失する可能性の追跡を処理します。](coordinate-systems-in-directx.md#handling-tracking-loss)
