---
title: アプリ内購入
description: アプリ内購入は、複合現実アプリでサポートされますが、それらを設定するには、いくつか作業があります。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ内購入、hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602881"
---
# <a name="in-app-purchases"></a><span data-ttu-id="ff469-104">アプリ内購入</span><span class="sxs-lookup"><span data-stu-id="ff469-104">In-app purchases</span></span>

<span data-ttu-id="ff469-105">アプリ内購入は、HoloLens でサポートされますが、それらを設定するには、いくつか作業があります。</span><span class="sxs-lookup"><span data-stu-id="ff469-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="ff469-106">アプリの購入を利用するために、機能する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff469-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="ff469-107">作成、XAML [2D ビュー](app-views.md)スレート型として表示するには</span><span class="sxs-lookup"><span data-stu-id="ff469-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="ff469-108">没入型のビューを離れる配置をアクティブ化するために切り替える</span><span class="sxs-lookup"><span data-stu-id="ff469-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="ff469-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="ff469-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="ff469-110">この API は、アプリ内購入の名前、説明、および価格を表示する株価の Windows OS ポップアップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff469-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="ff469-111">ユーザーは、購入に関するオプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="ff469-111">The user can then choose purchase options.</span></span> <span data-ttu-id="ff469-112">アプリは、ユーザーに戻るには、UI を提示する必要がありますアクションが完了すると、その[没入型ビュー](app-views.md)します。</span><span class="sxs-lookup"><span data-stu-id="ff469-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="ff469-113">デスクトップ ベースの Windows Mixed Reality イマーシブ ヘッドセットを対象としたアプリ、RequestProductPurchaseAsync API を呼び出す前に、XAML ビューに手動で切り替えることは必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ff469-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
