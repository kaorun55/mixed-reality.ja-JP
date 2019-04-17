---
title: 深さのカメラのホワイト ペーパー」ISSCC 2018
description: テクニカル ホワイト ペーパーで Azure と HoloLens の次のバージョンにプロジェクトの Kinect で使用する深度カメラをについて説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 7/5/2018
ms.topic: article
keywords: イベント、iscc、コンピューター ビジョン、調査、kinect、hololens、深さ、図表
ms.openlocfilehash: b692f9deeb7768e57ab6161b2c356a6610f18ed9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601084"
---
# <a name="depth-camera-whitepaper---isscc-2018"></a><span data-ttu-id="fc803-104">深さのカメラのホワイト ペーパー」ISSCC 2018</span><span class="sxs-lookup"><span data-stu-id="fc803-104">Depth camera whitepaper - ISSCC 2018</span></span>

<span data-ttu-id="fc803-105">**タイトル:** 1Mpixel 65 nm BSI 320 MHz 変調 3.5μm とイメージ センサーを大量に登録を解除グローバル シャッター ピクセル、アナログ ビン分割</span><span class="sxs-lookup"><span data-stu-id="fc803-105">**Title:** 1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning</span></span>

<span data-ttu-id="fc803-106">**寄稿者:** Cyrus S Bamji Swati Mehta、Barry Thompson、作成者: Tamer Elkhatib、Stefan Wurster、Onur Akkaya、Andrew ペイン、John Godbaz、Mike Fenton、Vijay Rajasekaran、Larry Prather、Satya Nagaraja、Vishali Mogallapu、Dane 雪、豊富なマコーレー Mustansir Mukadam、Iskender Agi、Shaun McCarthy、Zhanping Xu、Travis Perry、William Qian、Vei Han Chan、Prabhu Adepu、Gazi Ali、Muneeb Ahmed、Aditya Mukherjee、Sheethal Nayak、Dave Gampell、Sunil Acharya、Lou Kordus、Pat O'Connor</span><span class="sxs-lookup"><span data-stu-id="fc803-106">**Contributors:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Snow, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span></span>

<span data-ttu-id="fc803-107">**ISSCC 2018 で表示され、ISSCC Deg で公開します。技術です。ペーパー、Feb 2018 します。**</span><span class="sxs-lookup"><span data-stu-id="fc803-107">**Presented at ISSCC 2018 and published in ISSCC Deg. Tech. Papers, Feb 2018.**</span></span>

<span data-ttu-id="fc803-108">C.</span><span class="sxs-lookup"><span data-stu-id="fc803-108">C.</span></span> <span data-ttu-id="fc803-109">Bamji 副次的、"1Mpixel 65 nm BSI 320 MHz 変調 3.5μm とイメージ センサーを大量に登録を解除グローバル シャッター ピクセル、アナログ ビン分割では、"ISSCC Deg します。</span><span class="sxs-lookup"><span data-stu-id="fc803-109">Bamji et al., “1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning,” ISSCC Deg.</span></span> <span data-ttu-id="fc803-110">技術です。</span><span class="sxs-lookup"><span data-stu-id="fc803-110">Tech.</span></span> <span data-ttu-id="fc803-111">ペーパー、pp. 94 ~ 95、Feb 2018</span><span class="sxs-lookup"><span data-stu-id="fc803-111">Papers, pp. 94-95, Feb 2018.</span></span> <span data-ttu-id="fc803-112">IEEE リンクの詳細します。 https://ieeexplore.ieee.org/document/8310200/</span><span class="sxs-lookup"><span data-stu-id="fc803-112">IEEE Explore Link: https://ieeexplore.ieee.org/document/8310200/</span></span>

<span data-ttu-id="fc803-113">© 2018 IEEE.</span><span class="sxs-lookup"><span data-stu-id="fc803-113">© 2018 IEEE.</span></span> <span data-ttu-id="fc803-114">この資料の個人的な使用を許可します。</span><span class="sxs-lookup"><span data-stu-id="fc803-114">Personal use of this material is permitted.</span></span> <span data-ttu-id="fc803-115">再印刷再パブリッシュ宣伝または販売促進の目的で、再販またはサーバーや、リストへの再配布用の新しい集合的な動作を作成するには、このマテリアルを含む、現在または将来メディアにおいて、他のすべての使用 IEEE からのアクセス許可を取得する必要がありますかこの作業では、他の作品の著作権で保護されたコンポーネントの再利用します。</span><span class="sxs-lookup"><span data-stu-id="fc803-115">Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.</span></span>

<span data-ttu-id="fc803-116">**ホワイト ペーパー:**</span><span class="sxs-lookup"><span data-stu-id="fc803-116">**Whitepaper:**</span></span><br>
<span data-ttu-id="fc803-117">![ホワイト ペーパーのプレビュー](images/depth-camera-isscc.PNG)</span><span class="sxs-lookup"><span data-stu-id="fc803-117">![Preview of whitepaper](images/depth-camera-isscc.PNG)</span></span><br>
[<span data-ttu-id="fc803-118">深さのカメラに関するホワイト ペーパーをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="fc803-118">Download depth camera whitepaper</span></span>](images/Depth-Camera-ISSCC-2018.pdf)
