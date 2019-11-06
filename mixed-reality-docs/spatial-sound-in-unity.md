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
# <a name="spatial-sound-in-unity"></a>Unity の空間サウンド

このページでは、Unity mixed reality プロジェクトで Microsoft HRTF spatializer を使用および設計する際に役立つリソースにリンクしています。

## <a name="enable-spatialization"></a>Spatialization を有効にする

プロジェクトのオーディオ設定で**MS HRTF Spatializer**を有効にします。 詳細については、 [Unity の spatializer のドキュメント](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)を参照してください。 

階層内のオブジェクトに**オーディオソース**をアタッチし、 **[enable spatialization]** チェックボックスをオンにして **[空間 Blend]** スライダーを [1] に移動して、spatialization を有効にします。 詳細については、 [Unity のオーディオソースのドキュメント](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)を参照してください。 

## <a name="design-with-spatialization"></a>Spatialization を使用した設計

### <a name="distance-based-attenuation"></a>距離ベースの減衰
Unity の既定の距離ベースの減衰には、最小距離は1メーター、最大距離は500メートル、対数のロールアウトがあります。 これは、シナリオによっては機能します。また、ソースが急激に減少したり、速度が低下したりする可能性があります。 距離の減衰曲線の推奨設定については、「 [mixed reality のサウンドデザイン](spatial-sound-design.md)」を参照してください。 unity でこれらの曲線を設定する方法の詳細については、 [unity のオーディオソースのドキュメント](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)を参照してください。

### <a name="environment"></a>環境
**MS HRTF Spatializer**には、 [4 つのリバーブ設定](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment)と既定値 "small" を持つ部屋リバーブコンポーネントが含まれています。 ルーム設定は、spatialized オーディオソースを持つ Unity の各オブジェクトに次C#のスクリプトをアタッチすることで、プログラムによってオーディオソースごとに変更できます。

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

## <a name="unity-spatial-sound-examples"></a>Unity の空間サウンドの例
Mixed Reality Toolkit (MRTK) には、mixed reality でオーディオ効果を適用する方法の例が含まれています。 [Mrtk のデモ](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)です。

