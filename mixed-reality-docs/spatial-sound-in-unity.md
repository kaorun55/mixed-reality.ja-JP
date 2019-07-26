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
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="5a6ed-104">Unity の空間サウンド</span><span class="sxs-lookup"><span data-stu-id="5a6ed-104">Spatial sound in Unity</span></span>

<span data-ttu-id="5a6ed-105">このトピックでは、Unity プロジェクトで空間サウンドを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="5a6ed-106">ここでは、必要なプラグインファイルと、空間サウンドを有効にする Unity コンポーネントおよびプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="5a6ed-107">Unity での空間サウンドの有効化</span><span class="sxs-lookup"><span data-stu-id="5a6ed-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="5a6ed-108">Unity では、空間サウンドは audio spatializer プラグインを使用して有効になっています。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="5a6ed-109">プラグインファイルは Unity に直接バンドルされているため、空間サウンドを有効にするには、 **> プロジェクト設定を編集**し、音声を > し、インスペクターの**Spatializer プラグイン**を**MS HRTF Spatializer**に変更します。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="5a6ed-110">Microsoft spatializer では現在、48000Hz のみがサポートされているため、システムの出力デバイスが48000に設定されていない場合、まれに HRTF の障害が発生しないように、システムのサンプルレートを48000に設定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="5a6ed-111">![AudioManager 用のインスペクター](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="5a6ed-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="5a6ed-112">*AudioManager 用のインスペクター*</span><span class="sxs-lookup"><span data-stu-id="5a6ed-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="5a6ed-113">これで、Unity プロジェクトは、空間サウンドを使用するように構成されました。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="5a6ed-114">開発に Windows 10 PC を使用していない場合は、エディターまたはデバイス (Windows 10 SDK を使用している場合でも) では、空間サウンドが表示されません。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="5a6ed-115">Unity での空間サウンドの使用</span><span class="sxs-lookup"><span data-stu-id="5a6ed-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="5a6ed-116">空間サウンドは、オーディオソースコンポーネントの3つの設定を調整することによって、Unity プロジェクトで使用されます。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="5a6ed-117">次の手順では、空間サウンド用にオーディオソースコンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="5a6ed-118">[**階層**] パネルで、**オーディオソース**が接続されている game オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="5a6ed-119">[**インスペクター** ] パネルの [**オーディオソース**] コンポーネントで、</span><span class="sxs-lookup"><span data-stu-id="5a6ed-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="5a6ed-120">**Spatialize**オプションを確認します。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="5a6ed-121">**空間 Blend**を**3d** (数値 1) に設定します。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="5a6ed-122">最適な結果を得るには、[ **3D サウンド設定**] を展開し、[**ボリュームロール**アウト] を [**カスタムロールオフ**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="5a6ed-123">![オーディオソースを表示している Unity のインスペクターパネル](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="5a6ed-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="5a6ed-124">*オーディオソースを表示している Unity のインスペクターパネル*</span><span class="sxs-lookup"><span data-stu-id="5a6ed-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="5a6ed-125">これで、プロジェクトの環境内にサウンドが現実に存在するようになりました。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="5a6ed-126">[空間サウンドのデザインガイドライン](spatial-sound-design.md)について理解しておくことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="5a6ed-127">これらのガイドラインは、オーディオをプロジェクトにシームレスに統合し、ユーザーに対して作成したエクスペリエンスをさらにこちらするために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="5a6ed-128">空間サウンド設定の設定</span><span class="sxs-lookup"><span data-stu-id="5a6ed-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="5a6ed-129">Microsoft 空間サウンドプラグインには、オーディオソースごとに設定できる追加のパラメーターが用意されており、オーディオシミュレーションをさらに制御できます。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="5a6ed-130">このパラメーターは、シミュレートされたルームのサイズです。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="5a6ed-131">部屋のサイズ</span><span class="sxs-lookup"><span data-stu-id="5a6ed-131">Room Size</span></span>

<span data-ttu-id="5a6ed-132">空間サウンドによってシミュレートされているルームのサイズ。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="5a6ed-133">ルームのおおよそのサイズは、です。s (小規模な会議室のオフィス)、中程度 (大規模な会議室)、大規模 (聴衆)。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="5a6ed-134">また、部屋のサイズを [なし] に指定して、屋外環境をシミュレートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="5a6ed-135">既定の部屋のサイズは小です。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="5a6ed-136">例</span><span class="sxs-lookup"><span data-stu-id="5a6ed-136">Example</span></span>

<span data-ttu-id="5a6ed-137">MixedRealityToolkit for Unity は、空間サウンド設定を簡単に設定できるようにする静的クラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="5a6ed-138">このクラスは[MixedRealityToolkit\SpatialSound フォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound)にあり、プロジェクト内の任意のスクリプトから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="5a6ed-139">これらのパラメーターは、プロジェクトの各オーディオソースコンポーネントで設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="5a6ed-140">次の例では、接続されているオーディオソースの中規模の部屋のサイズを選択します。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="5a6ed-141">Unity から直接パラメーターにアクセスする</span><span class="sxs-lookup"><span data-stu-id="5a6ed-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="5a6ed-142">MixedRealityToolkit で優れたオーディオツールを使用しない場合は、HRTF パラメーターを変更する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="5a6ed-143">これをコピーして、 *SetHRTF.cs*という名前のスクリプトに貼り付けることができます。このスクリプトは、すべての HRTF audiosource にアタッチすることができます。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="5a6ed-144">HRTF にとって重要なパラメーターを変更できます。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-144">It lets you change parameters important to HRTF.</span></span>

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="5a6ed-145">混合 Reality ツールキットの空間サウンド</span><span class="sxs-lookup"><span data-stu-id="5a6ed-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="5a6ed-146">HoloToolkit-Examples/SpatialSound/シーン/UAudioManagerTest. unity</span><span class="sxs-lookup"><span data-stu-id="5a6ed-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="5a6ed-147">Mixed Reality Toolkit の次の例は、サウンドを使用してより多くの機能を体験する方法を示す一般的なオーディオ効果の例です。</span><span class="sxs-lookup"><span data-stu-id="5a6ed-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="5a6ed-148">HoloToolkit-Examples/SpatialSound/シーン/AudioLoFiTest</span><span class="sxs-lookup"><span data-stu-id="5a6ed-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="5a6ed-149">HoloToolkit-Examples/SpatialSound/シーン/AudioOcclusionTest</span><span class="sxs-lookup"><span data-stu-id="5a6ed-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="5a6ed-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a6ed-150">See also</span></span>
* [<span data-ttu-id="5a6ed-151">立体音響</span><span class="sxs-lookup"><span data-stu-id="5a6ed-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="5a6ed-152">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="5a6ed-152">Spatial sound design</span></span>](spatial-sound-design.md)
