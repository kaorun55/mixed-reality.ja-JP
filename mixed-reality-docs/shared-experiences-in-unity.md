---
title: Unity での共有エクスペリエンス
description: Unity アプリケーションで複数のユーザーの間で同じホログラムを共有します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共有、アンカー、WorldAnchor、MR WorldAnchorTransferBatch、SpatialPerception、Azure、Azure の空間アンカー、ASA は 250 の共有
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605071"
---
# <a name="shared-experiences-in-unity"></a>Unity での共有エクスペリエンス

共有エクスペリエンスは、複数のユーザーがそれぞれに独自の HoloLens、iOS または Android デバイスで、まとめて表示および対話が空間の固定位置に配置されている同じホログラムです。 これは、空間アンカーを共有することによって実現されます。

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

使用することができます<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>アンカーを作成する永続的なクラウド バックアップ空間、アプリが複数の HoloLens、iOS や Android デバイスで見つけることができますし、これです。  各ユーザーは複数のデバイスで共通の空間アンカーを共有することで、同じ物理的な場所でそのアンカーの基準としたコンテンツを表示できます。  これにより、リアルタイムのエクスペリエンスを共有します。

使用することも<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a> HoloLens、iOS および Android デバイスの間で非同期ホログラム永続化します。  持続性のあるクラウド空間アンカーを共有することで複数のデバイスはこれらのデバイスがまとめてと同時に存在しない場合でも、時間の経過と共に同じ永続化されたホログラムを確認できます。

5 分間試して、Unity での共有エクスペリエンスの構築を開始、<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">空間アンカー Unity の Azure クイック スタート</a>します。

空間のアンカーを Azure で稼働しているを開発したとして、<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">を作成し、Unity 内でアンカーを検索</a>します。

## <a name="local-anchor-transfers"></a>ローカルのアンカーの転送

Azure の空間アンカーを使用することはできませんの状況で[ローカル アンカー転送](local-anchor-transfers-in-unity.md)2 番目の HoloLens デバイスによってインポートされるアンカーをエクスポートする 1 つの HoloLens デバイスを有効にします。  このアプローチは、Azure の空間アンカーよりも堅牢性のアンカー再現率を提供し、iOS および Android デバイスは、このアプローチではサポートされていないことに注意してください。

## <a name="see-also"></a>関連項目
* [複合現実での経験を共有](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure の空間アンカー</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー Unity 用の SDK</a>