---
title: Unity の空間サウンド
description: Unity シーン内の特定の3D ポイントから取得した空間サウンドを再生します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、空間サウンド、HRTF、部屋サイズ
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549082"
---
# <a name="spatial-sound-in-unity"></a>Unity の空間サウンド

このトピックでは、Unity プロジェクトで空間サウンドを使用する方法について説明します。 ここでは、必要なプラグインファイルと、空間サウンドを有効にする Unity コンポーネントおよびプロパティについて説明します。

## <a name="enabling-spatial-sound-in-unity"></a>Unity での空間サウンドの有効化

Unity では、空間サウンドは audio spatializer プラグインを使用して有効になっています。 プラグインファイルは Unity に直接バンドルされているため、空間サウンドを有効にするには、 **> プロジェクト設定を編集**し、音声を > し、インスペクターの**Spatializer プラグイン**を**MS HRTF Spatializer**に変更します。 Microsoft spatializer では現在、48000Hz のみがサポートされているため、システムの出力デバイスが48000に設定されていない場合、まれに HRTF の障害が発生しないように、システムのサンプルレートを48000に設定する必要もあります。

![AudioManager 用のインスペクター](images/audio-250px.png)<br>
*AudioManager 用のインスペクター*

これで、Unity プロジェクトは、空間サウンドを使用するように構成されました。

>[!NOTE]
>開発に Windows 10 PC を使用していない場合は、エディターまたはデバイス (Windows 10 SDK を使用している場合でも) では、空間サウンドが表示されません。

## <a name="using-spatial-sound-in-unity"></a>Unity での空間サウンドの使用

空間サウンドは、オーディオソースコンポーネントの3つの設定を調整することによって、Unity プロジェクトで使用されます。 次の手順では、空間サウンド用にオーディオソースコンポーネントを構成します。
* [**階層**] パネルで、**オーディオソース**が接続されている game オブジェクトを選択します。
* [**インスペクター** ] パネルの [**オーディオソース**] コンポーネントで、
    * **Spatialize**オプションを確認します。
    * **空間 Blend**を**3d** (数値 1) に設定します。
    * 最適な結果を得るには、[ **3D サウンド設定**] を展開し、[**ボリュームロール**アウト] を [**カスタムロールオフ**] に設定します。

![オーディオソースを表示している Unity のインスペクターパネル](images/audiosource.png)<br>
*オーディオソースを表示している Unity のインスペクターパネル*

これで、プロジェクトの環境内にサウンドが現実に存在するようになりました。

[空間サウンドのデザインガイドライン](spatial-sound-design.md)について理解しておくことを強くお勧めします。 これらのガイドラインは、オーディオをプロジェクトにシームレスに統合し、ユーザーに対して作成したエクスペリエンスをさらにこちらするために役立ちます。

## <a name="setting-spatial-sound-settings"></a>空間サウンド設定の設定

Microsoft 空間サウンドプラグインには、オーディオソースごとに設定できる追加のパラメーターが用意されており、オーディオシミュレーションをさらに制御できます。 このパラメーターは、シミュレートされたルームのサイズです。

### <a name="room-size"></a>部屋のサイズ

空間サウンドによってシミュレートされているルームのサイズ。 ルームのおおよそのサイズは、です。s (小規模な会議室のオフィス)、中程度 (大規模な会議室)、大規模 (聴衆)。 また、部屋のサイズを [なし] に指定して、屋外環境をシミュレートすることもできます。 既定の部屋のサイズは小です。

### <a name="example"></a>例

MixedRealityToolkit for Unity は、空間サウンド設定を簡単に設定できるようにする静的クラスを提供します。 このクラスは[MixedRealityToolkit\SpatialSound フォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound)にあり、プロジェクト内の任意のスクリプトから呼び出すことができます。 これらのパラメーターは、プロジェクトの各オーディオソースコンポーネントで設定することをお勧めします。 次の例では、接続されているオーディオソースの中規模の部屋のサイズを選択します。

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Unity から直接パラメーターにアクセスする

MixedRealityToolkit で優れたオーディオツールを使用しない場合は、HRTF パラメーターを変更する方法を次に示します。 これをコピーして、 *SetHRTF.cs*という名前のスクリプトに貼り付けることができます。このスクリプトは、すべての HRTF audiosource にアタッチすることができます。 HRTF にとって重要なパラメーターを変更できます。

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>混合 Reality ツールキットの空間サウンド
- [HoloToolkit-Examples/SpatialSound/シーン/UAudioManagerTest. unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

Mixed Reality Toolkit の次の例は、サウンドを使用してより多くの機能を体験する方法を示す一般的なオーディオ効果の例です。
- [HoloToolkit-Examples/SpatialSound/シーン/AudioLoFiTest](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/シーン/AudioOcclusionTest](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>関連項目
* [立体音響](spatial-sound.md)
* [立体音響の設計](spatial-sound-design.md)
