---
title: Unreal のパフォーマンスに関する推奨事項
description: Unreal の Mixed Reality アプリで最適なパフォーマンスを得るための推奨事項
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, パフォーマンス, 最適化, 設定, ドキュメント
ms.openlocfilehash: 3c65eb519b57457e6c9e9747af0ad75e6a5e1b4d
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330197"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="6cc51-104">Unreal のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="6cc51-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="6cc51-105">概要</span><span class="sxs-lookup"><span data-stu-id="6cc51-105">Overview</span></span>

<span data-ttu-id="6cc51-106">この記事は、[Mixed Reality のパフォーマンスに関する推奨事項](understanding-performance-for-mixed-reality.md)についての記事の内容が基になっていますが、Unreal Engine に固有の学習に焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="6cc51-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="6cc51-107">続行する前に、アプリケーションのボトルネック、Mixed Reality アプリの分析とプロファイリング、および一般的なパフォーマンスの修正について確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6cc51-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="6cc51-108">推奨される Unreal プロジェクト設定を使用する</span><span class="sxs-lookup"><span data-stu-id="6cc51-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="6cc51-109">以下の各設定は、 **[編集] > [プロジェクトの設定]** にあります。</span><span class="sxs-lookup"><span data-stu-id="6cc51-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="6cc51-110">Mobile VR レンダラーの使用:</span><span class="sxs-lookup"><span data-stu-id="6cc51-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="6cc51-111">**[プロジェクト]** セクションまでスクロールし、 **[ターゲット ハードウェア]** を選択して、ターゲット プラットフォームを **[モバイル/タブレット]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="6cc51-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![モバイル ターゲット設定](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="6cc51-113">オクルージョン カリングの無効化:</span><span class="sxs-lookup"><span data-stu-id="6cc51-113">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="6cc51-114">**[エンジン]** セクションまでスクロールし、 **[レンダリング]** を選択し、 **[カリング]** セクションを展開して、 **[オクルージョン カリング]** をオフにします。</span><span class="sxs-lookup"><span data-stu-id="6cc51-114">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="6cc51-115">レンダリングされる詳細なシーンのオクルージョン カリングが必要な場合は、 **[エンジン] > [レンダリング]** で **[ソフトウェア オクルージョン カリングのサポート]** を有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6cc51-115">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Cullin** in **Engine > Rendering**.</span></span> <span data-ttu-id="6cc51-116">これにより、Unreal の作業は CPU 上で実行され、HoloLens 2 でのパフォーマンスが低い GPU オクルージョン クエリを回避できます。</span><span class="sxs-lookup"><span data-stu-id="6cc51-116">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>

![モバイル ターゲット設定](images/unreal/performance-recommendations-img-02.png)

3. <span data-ttu-id="6cc51-118">VR レンダリングの更新:</span><span class="sxs-lookup"><span data-stu-id="6cc51-118">Updating VR rendering:</span></span>
    * <span data-ttu-id="6cc51-119">**[エンジン]** セクションまでスクロールし、 **[レンダリング]** を選択し、 **[VR]** セクションを展開して、 **[インスタンス化ステレオ]** と **[モバイル マルチビュー]** の両方を有効にします。</span><span class="sxs-lookup"><span data-stu-id="6cc51-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span>
        + <span data-ttu-id="6cc51-120">**[Mobile Multi-View]\(モバイル マルチビュー\)** をオンにできるようにするために、 **[Mobile Post-Processing]\(モバイル後処理\)** をオフにすることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="6cc51-120">You may need to uncheck **Mobile Post-Processing** in order to be able to check **Mobile Multi-View**</span></span>

![モバイル ターゲット設定](images/unreal/performance-recommendations-img-03.png)
