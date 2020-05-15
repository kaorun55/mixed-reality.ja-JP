---
title: Unreal での空間アンカー
description: Unreal で空間アンカーを使用するためのガイド
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, 空間アンカー
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840141"
---
# <a name="spatial-anchors-in-unreal"></a>Unreal での空間アンカー

空間アンカーは、アプリケーション セッション間で現実世界の空間にホログラムを保持するために使用されます。  これは、Unreal では ARPin として示され、今後のセッションで読み込まれるように HoloLens のアンカー ストアに保存されます。 

アンカーを保存または読み込む前に、まずアンカー ストアの準備ができていることを確認します。  アンカー ストアの準備が整う前に、いずれかの HoloLens アンカー関数を呼び出そうとすると、失敗します。  

![空間アンカー ストア準備完了](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a>アンカーの保存

アプリケーションにコンポーネントがあり、それをワールドに固定する必要がある場合は、次のシーケンスを使用してアンカー ストアに保存できます。 

![空間アンカーの保存](images/unreal-spatialanchors-save.PNG)

ここでは、既知の位置にアクターを生成し、ARPin を (その位置と、アクターのクラスに基づいた名前を使用して) 作成します。そのアクターを ARPin に追加し、ピンを HoloLens アンカー ストアに保存します。  選択するアンカー名は一意である必要があるため、この例では現在のタイムスタンプを追加します。  アンカーがアンカー ストアに正常に保存された場合、HoloLens デバイス ポータルの [システム] > [Map manager]\(マップ マネージャー\) > [Anchor Files Saved On Device]\(デバイスに保存されたアンカー ファイル\) でそのアンカーを調べることができます。 

## <a name="load-anchors"></a>アンカーの読み込み

アプリケーションが起動すると、次のブループリントを呼び出して、コンポーネントをアンカー位置に復元できます。

![空間アンカーの読み込み](images/unreal-spatialanchors-load.PNG)

この例では、アンカー ストア内のすべてのアンカーを反復処理し、ID に対してアクターを生成し、そのアクターをアンカー ストアから ARPin にピン留めします。  アンカーは、保存された位置に基づいてワールドにホログラムを再配置する必要があるため、ID に対してアクターを生成することが重要です。そのため、ここで追加した変換によってアンカーにオフセットが追加されます。 

アンカーの保存された名前によって異なるアクターを生成できるように、アンカー ID も照会されます。 

## <a name="remove-anchors"></a>アンカーの削除 

アンカーを使い終わったら、アンカー ストア全体をクリアするか、アンカー ストアから個々のアンカーを削除して、後続のセッションに含まれないようにすることができます。 

![空間アンカーの削除](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a>関連項目
* [空間アンカー](spatial-anchors.md)
* [座標系](coordinate-systems.md)
