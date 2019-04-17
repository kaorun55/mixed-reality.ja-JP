---
title: Unity での空間のサウンド
description: 空間のサウンドの再生、Unity シーン内で特定 3D の点に由来します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、空間のサウンド HRTF、部屋のサイズ
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597514"
---
# <a name="spatial-sound-in-unity"></a>Unity での空間のサウンド

このトピックでは、Unity プロジェクトでサウンドの空間を使用する方法について説明します。 これは、必要なプラグイン ファイルだけでなく、Unity のコンポーネントと空間サウンドを有効にするプロパティについて説明します。

## <a name="enabling-spatial-sound-in-unity"></a>Unity での空間のサウンドを有効にします。

Unity での空間サウンドは、オーディオの立体音場プラグインを使用して有効です。 しようと同じくらい簡単には空間のサウンドを有効にするプラグイン ファイルが Unity に直接バンドルされる**編集 > プロジェクトの設定 > オーディオ**を変更して、**立体音場プラグイン**にインスペクター**MS HRTF 立体音場**します。 Microsoft 立体音の場はのみ、48000 Hz を現在サポートするためも 48000 こと、システムの出力デバイスに設定されていない 48000 既にまれなケースを HRTF エラーを防ぐために、システムのサンプル レートを設定してください。

![AudioManager についてインスペクター](images/audio-250px.png)<br>
*AudioManager についてインスペクター*

Unity プロジェクトは構成空間サウンドを使用するようになりました。

>[!NOTE]
>Windows 10 PC の開発を使用していない場合は取得されません空間サウンド、エディターにも、デバイス (Windows 10 SDK を使用している) 場合でも。

## <a name="using-spatial-sound-in-unity"></a>Unity でのサウンドの空間の使用

サウンドの空間は、オーディオ ソース コンポーネントに 3 つの設定を調整することによって、Unity プロジェクトで使用されます。 次の手順では、空間のサウンドをオーディオ ソース コンポーネントを構成します。
* **階層**パネルで、添付のゲーム オブジェクトを選択**オーディオ ソース**します。
* **インスペクター**パネルの**オーディオ ソース**コンポーネント
    * チェック、 **Spatialize**オプション。
    * 設定**空間 Blend**に**3D** (数値 1)。
    * 最良の結果を順に展開**3D サウンド設定**設定と**ボリューム ロールオフ**に**カスタム ロールオフ**します。

![Unity のオーディオ ソースの表示でインスペクター パネル](images/audiosource.png)<br>
*Unity のオーディオ ソースの表示でインスペクター パネル*

サウンドようになりました現実的内に存在して、プロジェクトの環境です。

理解を深めることを強くお勧め、[空間サウンドのデザイン ガイドライン](spatial-sound-design.md)します。 これらのガイドラインは、プロジェクトにオーディオをシームレスに統合して、作成したエクスペリエンスをさらに、ユーザーを利用できるのに役立ちます。

## <a name="setting-spatial-sound-settings"></a>空間のサウンド設定を設定

Microsoft 空間サウンド プラグインが設定できるで追加のパラメーターを提供します、オーディオ ソースごと、オーディオのシミュレーションの追加を制御できます。 このパラメーターは、シミュレートされた部屋のサイズです。

### <a name="room-size"></a>部屋のサイズ

空間のサウンドをシミュレートする、部屋のサイズ。 部屋のおおよそのサイズは、です。small (小規模な会議室に office)、medium (大会議室) と大きい (、聴衆)。 None 屋外の環境をシミュレートする部屋のサイズを指定することもできます。 既定の領域のサイズが小さです。

### <a name="example"></a>例

Unity の MixedRealityToolkit 空間サウンド設定を簡単に設定する静的クラスを提供します。 このクラスが記載されて、 [MixedRealityToolkit\SpatialSound フォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound)プロジェクト内のスクリプトから呼び出すことができます。 プロジェクトで、各オーディオ ソース コンポーネントでこれらのパラメーターを設定することをお勧めします。 接続されているオーディオ ソースの中規模の部屋のサイズを選択するとは、次の例です。

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Unity から直接パラメーターへのアクセス

オーディオの最適なツールを使用して、MixedRealityToolkit でない場合は、次 HRTF パラメーターを変更する方法に示します。 コピー/貼り付けするこのという名前のスクリプトに*SetHRTF.cs*すべて HRTF AudioSource にアタッチします。 HRTF に重要なパラメーターを変更できます。

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>Mixed Reality toolkit 空間のサウンド
- [HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

Mixed Reality Toolkit から次の例では、サウンドを使用して、エクスペリエンスを没入感が向上する方法を示すオーディオ効果の一般的な例を示します。
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>関連項目
* [空間のサウンド](spatial-sound.md)
* [サウンドの空間の設計](spatial-sound-design.md)
