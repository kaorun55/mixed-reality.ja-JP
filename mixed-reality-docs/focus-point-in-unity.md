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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604881"
---
# <a name="focus-point-in-unity"></a>Unity でのフォーカス ポイント

**名前空間:**  *UnityEngine.XR.WSA*<br>
**種類**:*HolographicSettings*

[フォーカス ポイント](hologram-stability.md#stabilization-plane)HoloLens、ホログラムを安定化を現在最も実行する方法についてのヒントの指定に設定されている表示できます。

Unity でフォーカス ポイントを設定する場合は、すべてのフレームを使用して設定する必要が*HolographicSettings.SetFocusPointForFrame()* します。 フォーカス ポイントがフレームに設定されていない場合、既定の安定化プレーンが使用されます。

> [!NOTE]
> 新しい Unity プロジェクトでは既定では、設定"を有効にする深度バッファーの共有 オプションがあります。  このオプションでは、没入型のデスクトップ ヘッドセットまたは Windows を実行している HoloLens のいずれかで実行されている Unity アプリ 10 April 2018 Update (RS4) 後では、アプリを指定せず、自動的にホログラム安定性を最適化するために Windows を深度バッファーを送信または、フォーカス ポイント:
> * 没入型のデスクトップ ヘッドセット、これにはピクセルあたりの深さに基づく reprojection 有効になります。
> * Windows を実行している、HoloLens 10 April 2018 Update または後で、分析、最適な安定化平面を自動的に選択する、深度バッファー。
>
> どちらの方法を提供より高い画質を明示的な作業なしフォーカス ポイントを選択するアプリによって各フレームします。  注意くださいフォーカス ポイントを手動で指定する場合と、上記で説明した自動動作をオーバーライド通常ホログラム安定性が削減されます。  一般に、する必要がありますだけを指定する手動のフォーカス ポイントを Windows に更新されていない HoloLens でアプリが実行されているときに 10 April 2018 Update。

### <a name="example"></a>例

使用可能なオーバー ロードで推奨されているとおり、フォーカス ポイントを設定する方法はたくさんあります、 *SetFocusPointForFrame*静的関数です。 次に示す各フレームを指定されたオブジェクトにフォーカス平面を設定する簡単な例を示します。

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

上記の単純なコードがホログラム安定性を減らす場合は、ユーザーの背後にある最終的にフォーカスがあるオブジェクトを終了することに注意してください。  これは、設定「を有効にする深度バッファーの共有」フォーカス ポイントを手動で指定する代わりにためにです。

### <a name="see-also"></a>関連項目
* [安定化プレーン](hologram-stability.md#stabilization-plane)
