---
title: Unreal のパフォーマンスに関する推奨事項
description: Unreal の Mixed Reality アプリで最適なパフォーマンスを得るための推奨事項
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, パフォーマンス, 最適化, 設定, ドキュメント
ms.openlocfilehash: a7972962eeb2b1480a7da38210b5ee77104f508b
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303639"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="71f69-104">Unreal のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="71f69-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="71f69-105">概要</span><span class="sxs-lookup"><span data-stu-id="71f69-105">Overview</span></span>

<span data-ttu-id="71f69-106">この記事は、[Mixed Reality のパフォーマンスに関する推奨事項](understanding-performance-for-mixed-reality.md)についての記事の内容が基になっていますが、Unreal Engine に固有の学習に焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="71f69-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="71f69-107">続行する前に、アプリケーションのボトルネック、Mixed Reality アプリの分析とプロファイリング、および一般的なパフォーマンスの修正について確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="71f69-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="71f69-108">推奨される Unreal プロジェクト設定を使用する</span><span class="sxs-lookup"><span data-stu-id="71f69-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="71f69-109">以下の各設定は、 **[編集] > [プロジェクトの設定]** にあります。</span><span class="sxs-lookup"><span data-stu-id="71f69-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="71f69-110">Mobile VR レンダラーの使用:</span><span class="sxs-lookup"><span data-stu-id="71f69-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="71f69-111">**[プロジェクト]** セクションまでスクロールし、 **[ターゲット ハードウェア]** を選択して、ターゲット プラットフォームを **[モバイル/タブレット]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="71f69-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![モバイル ターゲット設定](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="71f69-113">オクルージョン カリングの無効化:</span><span class="sxs-lookup"><span data-stu-id="71f69-113">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="71f69-114">**[エンジン]** セクションまでスクロールし、 **[レンダリング]** を選択し、 **[カリング]** セクションを展開して、 **[オクルージョン カリング]** をオフにします。</span><span class="sxs-lookup"><span data-stu-id="71f69-114">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="71f69-115">レンダリングされる詳細なシーンのオクルージョン カリングが必要な場合は、 **[エンジン] > [レンダリング]** で **[ソフトウェア オクルージョン カリングのサポート]** を有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="71f69-115">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="71f69-116">これにより、Unreal の作業は CPU 上で実行され、HoloLens 2 でのパフォーマンスが低い GPU オクルージョン クエリを回避できます。</span><span class="sxs-lookup"><span data-stu-id="71f69-116">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>

![オクルージョン カリングの無効化](images/unreal/performance-recommendations-img-02.png)

3. <span data-ttu-id="71f69-118">モバイル マルチビューの使用:</span><span class="sxs-lookup"><span data-stu-id="71f69-118">Using mobile multi-view:</span></span>
    * <span data-ttu-id="71f69-119">**[エンジン]** セクションまでスクロールし、 **[レンダリング]** を選択し、 **[VR]** セクションを展開して、 **[インスタンス化ステレオ]** と **[モバイル マルチビュー]** の両方を有効にします。</span><span class="sxs-lookup"><span data-stu-id="71f69-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="71f69-120">モバイル HDR をオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="71f69-120">Mobile HDR should be unchecked.</span></span>

![VR レンダリング設定](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="71f69-122">**[Maximum number of CSM cascades to render]\(レンダリングする CSM カスケードの最大数\)** を **1** に設定し、 **[Max Movable Spotlights / Point Lights]\(移動可能スポットライト / ポイント ライトの最大数\)** を **0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="71f69-122">Setting the **Maximum number of CSM cascades to render** to **1** and **Max Movable Spotlights / Point Lights** to **0**.</span></span> 
