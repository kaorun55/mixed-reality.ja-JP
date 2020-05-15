---
title: Unreal のパフォーマンスに関する推奨事項
description: Unreal の Mixed Reality アプリで最適なパフォーマンスを得るための推奨事項
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, パフォーマンス, 最適化, 設定, ドキュメント
ms.openlocfilehash: 1fab2f714628f61a518d89795cf644e90130200a
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840201"
---
# <a name="performance-recommendations-for-unreal"></a>Unreal のパフォーマンスに関する推奨事項

この記事は、[Mixed Reality のパフォーマンスに関する推奨事項](understanding-performance-for-mixed-reality.md)についての記事の内容が基になっていますが、Unreal Engine 環境に固有の学習に焦点を当てています。

## <a name="recommended-unreal-project-settings"></a>推奨される Unreal プロジェクト設定を使用する

- モバイル VR レンダラーを使用する - プロジェクト設定の [Project – Target Hardware]\(プロジェクト – ターゲット ハードウェア\) でターゲット プラットフォームを確実に [Mobile/Tablet]\(モバイル/タブレット\) に設定します。
- オクルージョン カリングを無効にする - [Culling]\(カリング\) セクションの [Engine – Rendering]\(エンジン – レンダリング\) で、[Occlusion Culling]\(オクルージョン カリング\) をオフにします。
    + 非常に詳細なシーンをレンダリングする必要があり、そのためにオクルージョン カリングが必要な場合は、[Engine – Rendering]\(エンジン – レンダリング\) で [Support Software Occlusion Culling]\(ソフトウェア オクルージョン カリングのサポート\) を有効にすることをお勧めします。 これにより、Unreal のオクルージョン カリングは CPU 上で実行され、HoloLens 2 でのパフォーマンスが低い GPU オクルージョン クエリを回避できます。
- [VR] カテゴリで [Engine – Rendering]\(エンジン – レンダリング\) の [Instanced Stereo] と [Mobile Multi-View]\(モバイル マルチビュー\) を両方とも有効にします。 [Mobile Multi-View]\(モバイル マルチビュー\) をオンにできるようにするために、[Mobile Post-Processing]\(モバイル後処理\) をオフにすることが必要な場合があります。
