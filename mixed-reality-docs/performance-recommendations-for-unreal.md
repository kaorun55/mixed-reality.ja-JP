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
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="910a8-104">Unreal のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="910a8-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="910a8-105">この記事は、[Mixed Reality のパフォーマンスに関する推奨事項](understanding-performance-for-mixed-reality.md)についての記事の内容が基になっていますが、Unreal Engine 環境に固有の学習に焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="910a8-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unreal Engine environment.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="910a8-106">推奨される Unreal プロジェクト設定を使用する</span><span class="sxs-lookup"><span data-stu-id="910a8-106">Recommended Unreal project settings</span></span>

- <span data-ttu-id="910a8-107">モバイル VR レンダラーを使用する - プロジェクト設定の [Project – Target Hardware]\(プロジェクト – ターゲット ハードウェア\) でターゲット プラットフォームを確実に [Mobile/Tablet]\(モバイル/タブレット\) に設定します。</span><span class="sxs-lookup"><span data-stu-id="910a8-107">Use the mobile VR renderer- in your project settings, ensure your target platform is set to "Mobile/Tablet" under "Project – Target Hardware"</span></span>
- <span data-ttu-id="910a8-108">オクルージョン カリングを無効にする - [Culling]\(カリング\) セクションの [Engine – Rendering]\(エンジン – レンダリング\) で、[Occlusion Culling]\(オクルージョン カリング\) をオフにします。</span><span class="sxs-lookup"><span data-stu-id="910a8-108">Disable occlusion culling- under "Engine – Rendering" in the "Culling" section, uncheck "Occlusion Culling"</span></span>
    + <span data-ttu-id="910a8-109">非常に詳細なシーンをレンダリングする必要があり、そのためにオクルージョン カリングが必要な場合は、[Engine – Rendering]\(エンジン – レンダリング\) で [Support Software Occlusion Culling]\(ソフトウェア オクルージョン カリングのサポート\) を有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="910a8-109">If occlusion culling is required because a very detailed scene needs to be rendered, it is recommended that "Support Software Occlusion Culling" is enabled Under "Engine – Rendering".</span></span> <span data-ttu-id="910a8-110">これにより、Unreal のオクルージョン カリングは CPU 上で実行され、HoloLens 2 でのパフォーマンスが低い GPU オクルージョン クエリを回避できます。</span><span class="sxs-lookup"><span data-stu-id="910a8-110">This allows Unreal to do occlusion culling on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
- <span data-ttu-id="910a8-111">[VR] カテゴリで [Engine – Rendering]\(エンジン – レンダリング\) の [Instanced Stereo] と [Mobile Multi-View]\(モバイル マルチビュー\) を両方とも有効にします。</span><span class="sxs-lookup"><span data-stu-id="910a8-111">Enable both "Instanced Stereo" and "Mobile Multi-View" under "Engine – Rendering" in the "VR" category.</span></span> <span data-ttu-id="910a8-112">[Mobile Multi-View]\(モバイル マルチビュー\) をオンにできるようにするために、[Mobile Post-Processing]\(モバイル後処理\) をオフにすることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="910a8-112">You may need to uncheck "Mobile Post-Processing" in order to be able to check "Mobile Multi-View"</span></span>
