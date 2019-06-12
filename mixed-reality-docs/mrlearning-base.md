---
title: MR Learning ベースのモジュールの概要
description: このコースでは、複合現実のアプリケーション内で Azure の顔認識機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 複合現実、unity、チュートリアル、hololens
ms.openlocfilehash: 2fe07efe87086e9a8c06e1953fcef8544b03c80a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829878"
---
# <a name="mr-learning-base-module-overview--objectives"></a><span data-ttu-id="8e2c9-104">目標 (&)、MR Learning ベースのモジュールの概要</span><span class="sxs-lookup"><span data-stu-id="8e2c9-104">MR Learning Base Module Overview & Objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="8e2c9-105">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="8e2c9-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8e2c9-106"><strong>コース</strong></span><span class="sxs-lookup"><span data-stu-id="8e2c9-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="8e2c9-107"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8e2c9-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="8e2c9-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="8e2c9-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="8e2c9-109"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="8e2c9-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="8e2c9-110">❌</span><span class="sxs-lookup"><span data-stu-id="8e2c9-110">❌</span></span></td>
        <td><span data-ttu-id="8e2c9-111">✔️</span><span class="sxs-lookup"><span data-stu-id="8e2c9-111">✔️</span></span></td>
        <td><span data-ttu-id="8e2c9-112">❌</span><span class="sxs-lookup"><span data-stu-id="8e2c9-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="8e2c9-113">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="8e2c9-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="8e2c9-114">前提条件</span><span class="sxs-lookup"><span data-stu-id="8e2c9-114">Prerequisites</span></span>

* <span data-ttu-id="8e2c9-115">正しく構成されている Windows 10 PC[ツールをインストール](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="8e2c9-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="8e2c9-116">Windows 10 SDK 10.0.18362.0 またはそれ以降</span><span class="sxs-lookup"><span data-stu-id="8e2c9-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="8e2c9-117">基本的なC#プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="8e2c9-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="8e2c9-118">HoloLens 2 デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。</span><span class="sxs-lookup"><span data-stu-id="8e2c9-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
