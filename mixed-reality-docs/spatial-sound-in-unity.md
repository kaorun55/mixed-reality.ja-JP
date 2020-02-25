---
title: Unity の空間サウンド
description: Unity シーン内の特定の3D ポイントから空間サウンドを再生します。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity、空間サウンド、HRTF、部屋サイズ
ms.openlocfilehash: 6720eac30c69ebfcd0f003cf131f60295818d676
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553700"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="01405-104">Unity の空間サウンド</span><span class="sxs-lookup"><span data-stu-id="01405-104">Spatial sound in Unity</span></span>

<span data-ttu-id="01405-105">このページでは、Unity の空間サウンドのリソースにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="01405-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="01405-106">Spatializer オプション</span><span class="sxs-lookup"><span data-stu-id="01405-106">Spatializer options</span></span>
<span data-ttu-id="01405-107">Mixed reality アプリケーションの Spatializer オプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="01405-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="01405-108">*MS HRTF Spatializer*。</span><span class="sxs-lookup"><span data-stu-id="01405-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="01405-109">Unity は、これを*Windows Mixed Reality*のオプションパッケージの一部として提供します。</span><span class="sxs-lookup"><span data-stu-id="01405-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="01405-110">これは、高コストの ' 単一ソース ' アーキテクチャの CPU 上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="01405-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="01405-111">これは、元の HoloLens アプリケーションとの下位互換性のために用意されています。</span><span class="sxs-lookup"><span data-stu-id="01405-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="01405-112">*Microsoft Spatializer*。</span><span class="sxs-lookup"><span data-stu-id="01405-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="01405-113">これは、 [Microsoft Spatializer GitHub リポジトリ](https://github.com/microsoft/spatialaudio-unity)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="01405-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="01405-114">これは、低コストの ' マルチソース ' アーキテクチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="01405-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="01405-115">HoloLens 2 では、これはハードウェアアクセラレータにオフロードされます。</span><span class="sxs-lookup"><span data-stu-id="01405-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="01405-116">新しいアプリケーションの場合は、 *Microsoft Spatializer*をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="01405-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="01405-117">Spatialization を有効にする</span><span class="sxs-lookup"><span data-stu-id="01405-117">Enable spatialization</span></span>

<span data-ttu-id="01405-118">[Unity の NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)を使用して_SpatialAudio_をインストールし、プロジェクトのオーディオ設定で**microsoft Spatializer**を選択します。</span><span class="sxs-lookup"><span data-stu-id="01405-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="01405-119">次のようになります。</span><span class="sxs-lookup"><span data-stu-id="01405-119">Then:</span></span>
* <span data-ttu-id="01405-120">階層内のオブジェクトに**オーディオソース**をアタッチする</span><span class="sxs-lookup"><span data-stu-id="01405-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="01405-121">**[Enable spatialization]** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="01405-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="01405-122">**空間ブレンド**スライダーを ' 1 ' に移動します</span><span class="sxs-lookup"><span data-stu-id="01405-122">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="01405-123">開発者ワークステーションで空間オーディオが有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="01405-123">Ensure spatial audio is enabled on your developer workstation.</span></span> <span data-ttu-id="01405-124">これを有効にするには、タスクバーのボリュームアイコンを右クリックし、[空間サウンド] が "オフ" 以外に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="01405-124">Enable it by right-clicking on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off."</span></span> <span data-ttu-id="01405-125">HoloLens 2 で聞く内容を最適に表示するには、 **[ヘッドホン用 Windows Sonic]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="01405-125">To get the best representation of what you'll hear on HoloLens 2, choose **Windows Sonic for Headphones**.</span></span>

<span data-ttu-id="01405-126">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01405-126">For more details, see:</span></span>
* [<span data-ttu-id="01405-127">Microsoft spatializer GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="01405-127">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="01405-128">Microsoft の spatializer チュートリアル</span><span class="sxs-lookup"><span data-stu-id="01405-128">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="01405-129">Unity のオーディオソースドキュメント</span><span class="sxs-lookup"><span data-stu-id="01405-129">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="01405-130">Unity の spatializer のドキュメント</span><span class="sxs-lookup"><span data-stu-id="01405-130">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="01405-131">距離ベースの減衰</span><span class="sxs-lookup"><span data-stu-id="01405-131">Distance-based attenuation</span></span>
<span data-ttu-id="01405-132">Unity の既定の距離ベースの減衰には、最小距離は1メーター、最大距離は500メートル、対数のロールアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="01405-132">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="01405-133">これらの設定は、シナリオによっては機能する場合があります。また、ソースが急激に増加したり、遅くなったりする場合もあります。</span><span class="sxs-lookup"><span data-stu-id="01405-133">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="01405-134">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01405-134">For more details, see:</span></span>
* <span data-ttu-id="01405-135">推奨設定のための[混合現実のサウンドデザイン](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="01405-135">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="01405-136">これらの曲線を設定する方法については、 [Unity のオーディオソースドキュメント](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01405-136">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="01405-137">ほど</span><span class="sxs-lookup"><span data-stu-id="01405-137">Reverb</span></span>
<span data-ttu-id="01405-138">_Microsoft Spatializer_は、既定で Spatializer 効果を無効にします。</span><span class="sxs-lookup"><span data-stu-id="01405-138">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="01405-139">Spatialized ソースに対してリバーブとその他の効果を有効にするには:</span><span class="sxs-lookup"><span data-stu-id="01405-139">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="01405-140">各ソースに**Room 効果の送信レベル**コンポーネントをアタッチする</span><span class="sxs-lookup"><span data-stu-id="01405-140">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="01405-141">各ソースの送信レベル曲線を調整して、エフェクト処理のためにグラフに返されるオーディオのゲインを制御します。</span><span class="sxs-lookup"><span data-stu-id="01405-141">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="01405-142">詳細について[は、spatializer チュートリアルの第5章](unity-spatial-audio-ch5.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01405-142">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="01405-143">Unity の空間サウンドの例</span><span class="sxs-lookup"><span data-stu-id="01405-143">Unity spatial sound examples</span></span>
<span data-ttu-id="01405-144">Unity の空間サウンドの例については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01405-144">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="01405-145">MRTK デモ</span><span class="sxs-lookup"><span data-stu-id="01405-145">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="01405-146">[Microsoft Spatializer サンプルプロジェクト](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="01405-146">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="01405-147">次のステップ:</span><span class="sxs-lookup"><span data-stu-id="01405-147">Next steps</span></span>
* [<span data-ttu-id="01405-148">混合現実におけるサウンドのデザイン</span><span class="sxs-lookup"><span data-stu-id="01405-148">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="01405-149">Microsoft の spatializer チュートリアル</span><span class="sxs-lookup"><span data-stu-id="01405-149">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)

