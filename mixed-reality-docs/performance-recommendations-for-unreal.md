---
title: Unreal のパフォーマンスに関する推奨事項
description: Unreal の Mixed Reality アプリで最適なパフォーマンスを得るための推奨事項
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, パフォーマンス, 最適化, 設定, ドキュメント
ms.openlocfilehash: 9f128a3ef09f29fc745c21b09b7ec97f5db33605
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533124"
---
# <a name="performance-recommendations-for-unreal"></a>Unreal のパフォーマンスに関する推奨事項

## <a name="overview"></a>概要

この記事は、[Mixed Reality のパフォーマンスに関する推奨事項](understanding-performance-for-mixed-reality.md)についての記事の内容が基になっていますが、Unreal Engine に固有の学習に焦点を当てています。 続行する前に、アプリケーションのボトルネック、Mixed Reality アプリの分析とプロファイリング、および一般的なパフォーマンスの修正について確認することをお勧めします。

## <a name="recommended-unreal-project-settings"></a>推奨される Unreal プロジェクト設定を使用する
以下の各設定は、 **[編集] > [プロジェクトの設定]** にあります。

1. Mobile VR レンダラーの使用:
    * **[プロジェクト]** セクションまでスクロールし、 **[ターゲット ハードウェア]** を選択して、ターゲット プラットフォームを **[モバイル/タブレット]** に設定します。

![モバイル ターゲット設定](images/unreal/performance-recommendations-img-01.png)

2. オクルージョン カリングの無効化:
    * **[エンジン]** セクションまでスクロールし、 **[レンダリング]** を選択し、 **[カリング]** セクションを展開して、 **[オクルージョン カリング]** をオフにします。
        + レンダリングされる詳細なシーンのオクルージョン カリングが必要な場合は、 **[エンジン] > [レンダリング]** で **[ソフトウェア オクルージョン カリングのサポート]** を有効にすることをお勧めします。 これにより、Unreal の作業は CPU 上で実行され、HoloLens 2 でのパフォーマンスが低い GPU オクルージョン クエリを回避できます。

![モバイル ターゲット設定](images/unreal/performance-recommendations-img-02.png)

3. VR レンダリングの更新:
    * **[エンジン]** セクションまでスクロールし、 **[レンダリング]** を選択し、 **[VR]** セクションを展開して、 **[インスタンス化ステレオ]** と **[モバイル マルチビュー]** の両方を有効にします。
        + **[Mobile Multi-View]\(モバイル マルチビュー\)** をオンにできるようにするために、 **[Mobile Post-Processing]\(モバイル後処理\)** をオフにすることが必要な場合があります。

![モバイル ターゲット設定](images/unreal/performance-recommendations-img-03.png)
