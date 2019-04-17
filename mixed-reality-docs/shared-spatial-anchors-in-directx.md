---
title: DirectX のアンカー空間の共有
description: 空間のアンカーを共有することで 2 つの HoloLens デバイスを同期する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、同期、空間アンカー、転送、マルチ プレーヤー、ビュー、シナリオ、チュートリアル、サンプル コード、Azure、Azure の空間アンカー、ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605061"
---
# <a name="shared-experiences-in-directx"></a>DirectX での共有エクスペリエンス

共有エクスペリエンスは、複数のユーザーがそれぞれに独自の HoloLens、iOS または Android デバイスで、まとめて表示および対話が空間の固定位置に配置されている同じホログラムです。 これは、空間アンカーを共有することによって実現されます。

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

使用することができます<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>アンカーを作成する永続的なクラウド バックアップ空間、アプリが複数の HoloLens、iOS や Android デバイスで見つけることができますし、これです。  各ユーザーは複数のデバイスで共通の空間アンカーを共有することで、同じ物理的な場所でそのアンカーの基準としたコンテンツを表示できます。  これにより、リアルタイムのエクスペリエンスを共有します。

使用することも<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a> HoloLens、iOS および Android デバイスの間で非同期ホログラム永続化します。  持続性のあるクラウド空間アンカーを共有することで複数のデバイスはこれらのデバイスがまとめてと同時に存在しない場合でも、時間の経過と共に同じ永続化されたホログラムを確認できます。

5 分間試して、HoloLens のアプリで共有のエクスペリエンスの構築を開始する、<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">空間アンカー HoloLens の Azure クイック スタート</a>します。

空間のアンカーを Azure で稼働しているを開発したとして、<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">を作成し、HoloLens でアンカーを見つける</a>します。  チュートリアルに利用<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android および iOS</a>同様に、すべてのデバイスで同じアンカーを共有できるようにすることです。

## <a name="local-anchor-transfers"></a>ローカルのアンカーの転送

Azure の空間アンカーを使用することはできませんの状況で[ローカル アンカー転送](local-anchor-transfers-in-directx.md)2 番目の HoloLens デバイスによってインポートされるアンカーをエクスポートする 1 つの HoloLens デバイスを有効にします。  このアプローチは、Azure の空間アンカーよりも堅牢性のアンカー再現率を提供し、iOS および Android デバイスは、このアプローチではサポートされていないことに注意してください。

## <a name="see-also"></a>関連項目
* [複合現実での経験を共有](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure の空間アンカー</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure 空間アンカー HoloLens の SDK</a>