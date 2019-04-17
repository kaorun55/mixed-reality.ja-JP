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
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="37a4d-104">Unity での空間のサウンド</span><span class="sxs-lookup"><span data-stu-id="37a4d-104">Spatial sound in Unity</span></span>

<span data-ttu-id="37a4d-105">このトピックでは、Unity プロジェクトでサウンドの空間を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37a4d-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="37a4d-106">これは、必要なプラグイン ファイルだけでなく、Unity のコンポーネントと空間サウンドを有効にするプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="37a4d-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="37a4d-107">Unity での空間のサウンドを有効にします。</span><span class="sxs-lookup"><span data-stu-id="37a4d-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="37a4d-108">Unity での空間サウンドは、オーディオの立体音場プラグインを使用して有効です。</span><span class="sxs-lookup"><span data-stu-id="37a4d-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="37a4d-109">しようと同じくらい簡単には空間のサウンドを有効にするプラグイン ファイルが Unity に直接バンドルされる**編集 > プロジェクトの設定 > オーディオ**を変更して、**立体音場プラグイン**にインスペクター**MS HRTF 立体音場**します。</span><span class="sxs-lookup"><span data-stu-id="37a4d-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="37a4d-110">Microsoft 立体音の場はのみ、48000 Hz を現在サポートするためも 48000 こと、システムの出力デバイスに設定されていない 48000 既にまれなケースを HRTF エラーを防ぐために、システムのサンプル レートを設定してください。</span><span class="sxs-lookup"><span data-stu-id="37a4d-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="37a4d-111">![AudioManager についてインスペクター](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="37a4d-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="37a4d-112">*AudioManager についてインスペクター*</span><span class="sxs-lookup"><span data-stu-id="37a4d-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="37a4d-113">Unity プロジェクトは構成空間サウンドを使用するようになりました。</span><span class="sxs-lookup"><span data-stu-id="37a4d-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="37a4d-114">Windows 10 PC の開発を使用していない場合は取得されません空間サウンド、エディターにも、デバイス (Windows 10 SDK を使用している) 場合でも。</span><span class="sxs-lookup"><span data-stu-id="37a4d-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="37a4d-115">Unity でのサウンドの空間の使用</span><span class="sxs-lookup"><span data-stu-id="37a4d-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="37a4d-116">サウンドの空間は、オーディオ ソース コンポーネントに 3 つの設定を調整することによって、Unity プロジェクトで使用されます。</span><span class="sxs-lookup"><span data-stu-id="37a4d-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="37a4d-117">次の手順では、空間のサウンドをオーディオ ソース コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="37a4d-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="37a4d-118">**階層**パネルで、添付のゲーム オブジェクトを選択**オーディオ ソース**します。</span><span class="sxs-lookup"><span data-stu-id="37a4d-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="37a4d-119">**インスペクター**パネルの**オーディオ ソース**コンポーネント</span><span class="sxs-lookup"><span data-stu-id="37a4d-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="37a4d-120">チェック、 **Spatialize**オプション。</span><span class="sxs-lookup"><span data-stu-id="37a4d-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="37a4d-121">設定**空間 Blend**に**3D** (数値 1)。</span><span class="sxs-lookup"><span data-stu-id="37a4d-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="37a4d-122">最良の結果を順に展開**3D サウンド設定**設定と**ボリューム ロールオフ**に**カスタム ロールオフ**します。</span><span class="sxs-lookup"><span data-stu-id="37a4d-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="37a4d-123">![Unity のオーディオ ソースの表示でインスペクター パネル](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="37a4d-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="37a4d-124">*Unity のオーディオ ソースの表示でインスペクター パネル*</span><span class="sxs-lookup"><span data-stu-id="37a4d-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="37a4d-125">サウンドようになりました現実的内に存在して、プロジェクトの環境です。</span><span class="sxs-lookup"><span data-stu-id="37a4d-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="37a4d-126">理解を深めることを強くお勧め、[空間サウンドのデザイン ガイドライン](spatial-sound-design.md)します。</span><span class="sxs-lookup"><span data-stu-id="37a4d-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="37a4d-127">これらのガイドラインは、プロジェクトにオーディオをシームレスに統合して、作成したエクスペリエンスをさらに、ユーザーを利用できるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="37a4d-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="37a4d-128">空間のサウンド設定を設定</span><span class="sxs-lookup"><span data-stu-id="37a4d-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="37a4d-129">Microsoft 空間サウンド プラグインが設定できるで追加のパラメーターを提供します、オーディオ ソースごと、オーディオのシミュレーションの追加を制御できます。</span><span class="sxs-lookup"><span data-stu-id="37a4d-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="37a4d-130">このパラメーターは、シミュレートされた部屋のサイズです。</span><span class="sxs-lookup"><span data-stu-id="37a4d-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="37a4d-131">部屋のサイズ</span><span class="sxs-lookup"><span data-stu-id="37a4d-131">Room Size</span></span>

<span data-ttu-id="37a4d-132">空間のサウンドをシミュレートする、部屋のサイズ。</span><span class="sxs-lookup"><span data-stu-id="37a4d-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="37a4d-133">部屋のおおよそのサイズは、です。small (小規模な会議室に office)、medium (大会議室) と大きい (、聴衆)。</span><span class="sxs-lookup"><span data-stu-id="37a4d-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="37a4d-134">None 屋外の環境をシミュレートする部屋のサイズを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="37a4d-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="37a4d-135">既定の領域のサイズが小さです。</span><span class="sxs-lookup"><span data-stu-id="37a4d-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="37a4d-136">例</span><span class="sxs-lookup"><span data-stu-id="37a4d-136">Example</span></span>

<span data-ttu-id="37a4d-137">Unity の MixedRealityToolkit 空間サウンド設定を簡単に設定する静的クラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="37a4d-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="37a4d-138">このクラスが記載されて、 [MixedRealityToolkit\SpatialSound フォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound)プロジェクト内のスクリプトから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="37a4d-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="37a4d-139">プロジェクトで、各オーディオ ソース コンポーネントでこれらのパラメーターを設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="37a4d-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="37a4d-140">接続されているオーディオ ソースの中規模の部屋のサイズを選択するとは、次の例です。</span><span class="sxs-lookup"><span data-stu-id="37a4d-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="37a4d-141">Unity から直接パラメーターへのアクセス</span><span class="sxs-lookup"><span data-stu-id="37a4d-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="37a4d-142">オーディオの最適なツールを使用して、MixedRealityToolkit でない場合は、次 HRTF パラメーターを変更する方法に示します。</span><span class="sxs-lookup"><span data-stu-id="37a4d-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="37a4d-143">コピー/貼り付けするこのという名前のスクリプトに*SetHRTF.cs*すべて HRTF AudioSource にアタッチします。</span><span class="sxs-lookup"><span data-stu-id="37a4d-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="37a4d-144">HRTF に重要なパラメーターを変更できます。</span><span class="sxs-lookup"><span data-stu-id="37a4d-144">It lets you change parameters important to HRTF.</span></span>

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="37a4d-145">Mixed Reality toolkit 空間のサウンド</span><span class="sxs-lookup"><span data-stu-id="37a4d-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="37a4d-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="37a4d-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="37a4d-147">Mixed Reality Toolkit から次の例では、サウンドを使用して、エクスペリエンスを没入感が向上する方法を示すオーディオ効果の一般的な例を示します。</span><span class="sxs-lookup"><span data-stu-id="37a4d-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="37a4d-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span><span class="sxs-lookup"><span data-stu-id="37a4d-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="37a4d-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span><span class="sxs-lookup"><span data-stu-id="37a4d-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="37a4d-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="37a4d-150">See also</span></span>
* [<span data-ttu-id="37a4d-151">空間のサウンド</span><span class="sxs-lookup"><span data-stu-id="37a4d-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="37a4d-152">サウンドの空間の設計</span><span class="sxs-lookup"><span data-stu-id="37a4d-152">Spatial sound design</span></span>](spatial-sound-design.md)
