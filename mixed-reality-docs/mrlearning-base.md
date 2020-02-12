---
title: 入門チュートリアル-1. 概要と目標
description: このコースでは、mixed reality アプリケーション内で Azure 顔認識を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: dbae7545edb6515b5cf148fbbfb6652595d2fc0d
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129263"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="9676d-105">1. 概要と目標</span><span class="sxs-lookup"><span data-stu-id="9676d-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="9676d-106">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="9676d-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9676d-107"><strong>まで</strong></span><span class="sxs-lookup"><span data-stu-id="9676d-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="9676d-108"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="9676d-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="9676d-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="9676d-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="9676d-110"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9676d-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="9676d-111">✔️</span><span class="sxs-lookup"><span data-stu-id="9676d-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="9676d-112">開始する前に</span><span class="sxs-lookup"><span data-stu-id="9676d-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9676d-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="9676d-113">Prerequisites</span></span>

* <span data-ttu-id="9676d-114">適切な[ツールがインストール](install-the-tools.md)されている WINDOWS 10 PC</span><span class="sxs-lookup"><span data-stu-id="9676d-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="9676d-115">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="9676d-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="9676d-116">基本的なC#プログラミング機能</span><span class="sxs-lookup"><span data-stu-id="9676d-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="9676d-117">[開発用に構成され](using-visual-studio.md#enabling-developer-mode)た HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="9676d-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="9676d-118">Unity 2019.2 がインストールされ、ユニバーサル Windows プラットフォームビルドサポートモジュールが追加された<a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity ハブ</a></span><span class="sxs-lookup"><span data-stu-id="9676d-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9676d-119">このチュートリアルシリーズで推奨されている Unity バージョンは Unity 2019.2 です。</span><span class="sxs-lookup"><span data-stu-id="9676d-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="9676d-120">これは、前にリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="9676d-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="9676d-121">次のレッスン: 2. プロジェクトと最初のアプリケーションの初期化</span><span class="sxs-lookup"><span data-stu-id="9676d-121">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)
