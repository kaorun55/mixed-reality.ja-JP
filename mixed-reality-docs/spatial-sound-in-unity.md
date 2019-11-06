---
title: Unity の空間サウンド
description: Unity シーン内の特定の3D ポイントから取得した空間サウンドを再生します。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity、空間サウンド、HRTF、部屋サイズ
ms.openlocfilehash: c96717d9df9b89fbb09f0b4466ee3a9bf5c8a149
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641071"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="c377b-104">Unity の空間サウンド</span><span class="sxs-lookup"><span data-stu-id="c377b-104">Spatial Sound in Unity</span></span>

<span data-ttu-id="c377b-105">このページでは、Unity mixed reality プロジェクトで Microsoft HRTF spatializer を使用および設計する際に役立つリソースにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="c377b-105">This page links to resources to help you use and design with the Microsoft HRTF spatializer in your Unity mixed reality projects.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="c377b-106">Spatialization を有効にする</span><span class="sxs-lookup"><span data-stu-id="c377b-106">Enable spatialization</span></span>

<span data-ttu-id="c377b-107">プロジェクトのオーディオ設定で**MS HRTF Spatializer**を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c377b-107">Enable the **MS HRTF Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="c377b-108">詳細については、 [Unity の spatializer のドキュメント](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c377b-108">For more details, see [Unity's spatializer documentation](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span></span> 

<span data-ttu-id="c377b-109">階層内のオブジェクトに**オーディオソース**をアタッチし、 **[enable spatialization]** チェックボックスをオンにして **[空間 Blend]** スライダーを [1] に移動して、spatialization を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c377b-109">Attach an **Audio Source** to an object in the hierarchy, and enable spatialization by checking the **Enable spatialization** checkbox and moving the **Spatial Blend** slider to '1'.</span></span> <span data-ttu-id="c377b-110">詳細については、 [Unity のオーディオソースのドキュメント](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c377b-110">For more details, see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span></span> 

## <a name="design-with-spatialization"></a><span data-ttu-id="c377b-111">Spatialization を使用した設計</span><span class="sxs-lookup"><span data-stu-id="c377b-111">Design with spatialization</span></span>

### <a name="distance-based-attenuation"></a><span data-ttu-id="c377b-112">距離ベースの減衰</span><span class="sxs-lookup"><span data-stu-id="c377b-112">Distance-based attenuation</span></span>
<span data-ttu-id="c377b-113">Unity の既定の距離ベースの減衰には、最小距離は1メーター、最大距離は500メートル、対数のロールアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="c377b-113">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="c377b-114">これは、シナリオによっては機能します。また、ソースが急激に減少したり、速度が低下したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c377b-114">This may work for your scenario, or you may find sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="c377b-115">距離の減衰曲線の推奨設定については、「 [mixed reality のサウンドデザイン](spatial-sound-design.md)」を参照してください。 unity でこれらの曲線を設定する方法の詳細については、 [unity のオーディオソースのドキュメント](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c377b-115">See [sound design in mixed reality](spatial-sound-design.md) for recommended settings for distance decay curves, and see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for information on setting these curves in Unity.</span></span>

### <a name="environment"></a><span data-ttu-id="c377b-116">環境</span><span class="sxs-lookup"><span data-stu-id="c377b-116">Environment</span></span>
<span data-ttu-id="c377b-117">**MS HRTF Spatializer**には、 [4 つのリバーブ設定](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment)と既定値 "small" を持つ部屋リバーブコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c377b-117">The **MS HRTF Spatializer** includes a room reverb component with [four reverb settings](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) and a default of 'small'.</span></span> <span data-ttu-id="c377b-118">ルーム設定は、spatialized オーディオソースを持つ Unity の各オブジェクトに次C#のスクリプトをアタッチすることで、プログラムによってオーディオソースごとに変更できます。</span><span class="sxs-lookup"><span data-stu-id="c377b-118">The room setting can be changed programmatically for each audio source by attaching the following C# script to each object in Unity that has a spatialized Audio Source:</span></span>

```cs
using UnityEngine;
   using System.Collections;
   public class SetHRTF : MonoBehaviour    {
       public enum ROOMSIZE { Small, Medium, Large, None };
       public ROOMSIZE room = ROOMSIZE.Small;  // Small is regarded as the "most average"
       // defaults and docs from MSDN
       // https://msdn.microsoft.com/library/windows/desktop/mt186602(v=vs.85).aspx
       AudioSource audiosource;
       void Awake()
       {
           audiosource = this.gameObject.GetComponent<AudioSource>();
           if (audiosource == null)
           {
               print("SetHRTFParams needs an audio source to do anything.");
               return;
           }
           audiosource.spatialize = 1; // we DO want spatialized audio
           audiosource.spread = 0; // we dont want to reduce our angle of hearing
           audiosource.spatialBlend = 1;   // we do want to hear spatialized audio
           audiosource.SetSpatializerFloat(1, (float)room);    // 1 is the roomsize param
       }
   }
```

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="c377b-119">Unity の空間サウンドの例</span><span class="sxs-lookup"><span data-stu-id="c377b-119">Unity spatial sound examples</span></span>
<span data-ttu-id="c377b-120">Mixed Reality Toolkit (MRTK) には、mixed reality でオーディオ効果を適用する方法の例が含まれています。 [Mrtk のデモ](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)です。</span><span class="sxs-lookup"><span data-stu-id="c377b-120">The Mixed Reality Toolkit (MRTK) includes examples of ways to apply audio effects in mixed reality: [MRTK demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span></span>

