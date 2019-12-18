---
title: Unity の空間サウンド
description: Unity シーン内の特定の3D ポイントから空間サウンドを再生します。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity、空間サウンド、HRTF、部屋サイズ
ms.openlocfilehash: 3e7d0ea231545d5112d182dffbc02f217ca4a4a7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181992"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="6e231-104">Unity の空間サウンド</span><span class="sxs-lookup"><span data-stu-id="6e231-104">Spatial sound in Unity</span></span>

<span data-ttu-id="6e231-105">このページでは、Unity の空間サウンドのリソースにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="6e231-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="6e231-106">Spatializer オプション</span><span class="sxs-lookup"><span data-stu-id="6e231-106">Spatializer options</span></span>
<span data-ttu-id="6e231-107">Mixed reality アプリケーションの Spatializer オプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6e231-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="6e231-108">*MS HRTF Spatializer*。</span><span class="sxs-lookup"><span data-stu-id="6e231-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="6e231-109">Unity は、これを*Windows Mixed Reality*のオプションパッケージの一部として提供します。</span><span class="sxs-lookup"><span data-stu-id="6e231-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="6e231-110">これは、高コストの ' 単一ソース ' アーキテクチャの CPU 上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="6e231-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="6e231-111">これは、元の HoloLens アプリケーションとの下位互換性のために用意されています。</span><span class="sxs-lookup"><span data-stu-id="6e231-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="6e231-112">*Microsoft Spatializer*。</span><span class="sxs-lookup"><span data-stu-id="6e231-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="6e231-113">これは、 [Microsoft Spatializer GitHub リポジトリ](https://github.com/microsoft/spatialaudio-unity)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="6e231-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="6e231-114">これは、低コストの ' マルチソース ' アーキテクチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="6e231-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="6e231-115">HoloLens 2 では、これはハードウェアアクセラレータにオフロードされます。</span><span class="sxs-lookup"><span data-stu-id="6e231-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="6e231-116">新しいアプリケーションの場合は、 *Microsoft Spatializer*をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6e231-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="6e231-117">Spatialization を有効にする</span><span class="sxs-lookup"><span data-stu-id="6e231-117">Enable spatialization</span></span>

<span data-ttu-id="6e231-118">[Unity の NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)を使用して_SpatialAudio_をインストールし、プロジェクトのオーディオ設定で**microsoft Spatializer**を選択します。</span><span class="sxs-lookup"><span data-stu-id="6e231-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="6e231-119">さらに、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6e231-119">Then:</span></span>
* <span data-ttu-id="6e231-120">階層内のオブジェクトに**オーディオソース**をアタッチする</span><span class="sxs-lookup"><span data-stu-id="6e231-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="6e231-121">**[Enable spatialization]** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6e231-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="6e231-122">**空間ブレンド**スライダーを ' 1 ' に移動します</span><span class="sxs-lookup"><span data-stu-id="6e231-122">Move the **Spatial Blend** slider to '1'</span></span>

<span data-ttu-id="6e231-123">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e231-123">For more details, see:</span></span>
* [<span data-ttu-id="6e231-124">Microsoft spatializer GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="6e231-124">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="6e231-125">Microsoft の spatializer チュートリアル</span><span class="sxs-lookup"><span data-stu-id="6e231-125">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="6e231-126">Unity のオーディオソースドキュメント</span><span class="sxs-lookup"><span data-stu-id="6e231-126">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="6e231-127">Unity の spatializer のドキュメント</span><span class="sxs-lookup"><span data-stu-id="6e231-127">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="6e231-128">距離ベースの減衰</span><span class="sxs-lookup"><span data-stu-id="6e231-128">Distance-based attenuation</span></span>
<span data-ttu-id="6e231-129">Unity の既定の距離ベースの減衰には、最小距離は1メーター、最大距離は500メートル、対数のロールアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="6e231-129">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="6e231-130">これらの設定は、シナリオによっては機能する場合があります。また、ソースが急激に増加したり、遅くなったりする場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6e231-130">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="6e231-131">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e231-131">For more details, see:</span></span>
* <span data-ttu-id="6e231-132">推奨設定のための[混合現実のサウンドデザイン](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="6e231-132">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="6e231-133">これらの曲線を設定する方法については、 [Unity のオーディオソースドキュメント](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e231-133">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="6e231-134">ほど</span><span class="sxs-lookup"><span data-stu-id="6e231-134">Reverb</span></span>
<span data-ttu-id="6e231-135">_Microsoft Spatializer_は、既定で Spatializer 効果を無効にします。</span><span class="sxs-lookup"><span data-stu-id="6e231-135">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="6e231-136">Spatialized ソースに対してリバーブとその他の効果を有効にするには:</span><span class="sxs-lookup"><span data-stu-id="6e231-136">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="6e231-137">各ソースに**Room 効果の送信レベル**コンポーネントをアタッチする</span><span class="sxs-lookup"><span data-stu-id="6e231-137">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="6e231-138">各ソースの送信レベル曲線を調整して、エフェクト処理のためにグラフに返されるオーディオのゲインを制御します。</span><span class="sxs-lookup"><span data-stu-id="6e231-138">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="6e231-139">詳細について[は、spatializer チュートリアルの第5章](unity-spatial-audio-ch5.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e231-139">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="6e231-140">Unity の空間サウンドの例</span><span class="sxs-lookup"><span data-stu-id="6e231-140">Unity spatial sound examples</span></span>
<span data-ttu-id="6e231-141">Unity の空間サウンドの例については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e231-141">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="6e231-142">MRTK デモ</span><span class="sxs-lookup"><span data-stu-id="6e231-142">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="6e231-143">[Microsoft Spatializer サンプルプロジェクト](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="6e231-143">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="6e231-144">次のステップ</span><span class="sxs-lookup"><span data-stu-id="6e231-144">Next steps</span></span>
* [<span data-ttu-id="6e231-145">混合現実におけるサウンドのデザイン</span><span class="sxs-lookup"><span data-stu-id="6e231-145">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="6e231-146">Microsoft の spatializer チュートリアル</span><span class="sxs-lookup"><span data-stu-id="6e231-146">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)

