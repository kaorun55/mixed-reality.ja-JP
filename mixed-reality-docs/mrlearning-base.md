---
title: MR Learning ベースのモジュールの概要
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 389a23129d4dfc5819cdc45d071b678e3792089d
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523159"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="f26c5-104">1. 概要と目標</span><span class="sxs-lookup"><span data-stu-id="f26c5-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="f26c5-105">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="f26c5-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f26c5-106"><strong>コース</strong></span><span class="sxs-lookup"><span data-stu-id="f26c5-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="f26c5-107"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="f26c5-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="f26c5-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="f26c5-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="f26c5-109"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="f26c5-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="f26c5-110">❌</span><span class="sxs-lookup"><span data-stu-id="f26c5-110">❌</span></span></td>
        <td><span data-ttu-id="f26c5-111">✔️</span><span class="sxs-lookup"><span data-stu-id="f26c5-111">✔️</span></span></td>
        <td><span data-ttu-id="f26c5-112">❌</span><span class="sxs-lookup"><span data-stu-id="f26c5-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="f26c5-113">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="f26c5-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="f26c5-114">前提条件</span><span class="sxs-lookup"><span data-stu-id="f26c5-114">Prerequisites</span></span>

* <span data-ttu-id="f26c5-115">正しく構成されている Windows 10 PC[ツールをインストール](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="f26c5-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="f26c5-116">Windows 10 SDK 10.0.18362.0 またはそれ以降</span><span class="sxs-lookup"><span data-stu-id="f26c5-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="f26c5-117">基本的なC#プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="f26c5-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="f26c5-118">HoloLens 2 デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。</span><span class="sxs-lookup"><span data-stu-id="f26c5-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
