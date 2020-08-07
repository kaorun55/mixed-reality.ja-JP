# <a name="unity"></a>[<span data-ttu-id="cb2f3-101">Unity</span><span class="sxs-lookup"><span data-stu-id="cb2f3-101">Unity</span></span>](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="cb2f3-103">1.最新バージョンをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="cb2f3-103">1. Download the latest version</span></span>

<span data-ttu-id="cb2f3-104">新しいプロジェクトを開始する際に使用する最適なバージョンとして、[Unity LTS (長期サポート)](https://unity3d.com/unity/qa/lts-releases) ストリームをお勧めします。最新の安定した修正プログラムを取得するには最新リビジョンに更新します。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span> 
* <span data-ttu-id="cb2f3-105">現在は、**Unity 2019** を使用することをお勧めしています。これは、以下の MRTK v2 に必要な LTS ビルドです。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-105">The current recommendation is to use **Unity 2019**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="cb2f3-106">特定の理由から別のバージョンの Unity を使用する必要がある場合、Unity では異なるバージョンの side-by-side インストールをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="cb2f3-107">2.Mixed Reality Toolkit (MRTK) をインポートする</span><span class="sxs-lookup"><span data-stu-id="cb2f3-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../images/UX/MRTK_UX_Hero.png)

<span data-ttu-id="cb2f3-109">[Mixed Reality Toolkit](../mrtk-getting-started.md) (MRTK) は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-109">[Mixed Reality Toolkit](../mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="cb2f3-110">MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="cb2f3-111">このツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="cb2f3-112"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="cb2f3-112"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="cb2f3-113">**Mixed Reality Toolkit-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="cb2f3-113">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="cb2f3-114">Unity 用の MRTK を使用しない場合は、すべての対話式操作と動作のスクリプトを開発者が自分で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-114">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="cb2f3-115">その他のツール (省略可能)</span><span class="sxs-lookup"><span data-stu-id="cb2f3-115">Other tools [optional]</span></span>
* <span data-ttu-id="cb2f3-116"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-116"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="cb2f3-117"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-117"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="cb2f3-118">3.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="cb2f3-118">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="cb2f3-119">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-119">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="cb2f3-120">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-120">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="cb2f3-121">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-121">Note that not all tools are supported on older operating systems.</span></span> 

> [!NOTE]
> <span data-ttu-id="cb2f3-122">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-122">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="cb2f3-123">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-123">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="cb2f3-124">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="cb2f3-124">For HoloLens development</span></span>

<span data-ttu-id="cb2f3-125">開発用の PC を HoloLens の開発用に設定するときは、<a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> と <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-125">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="cb2f3-126">[HoloLens エミュレーター](../using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-126">If you plan on using the [HoloLens emulator](../using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="cb2f3-127">HoloLens エミュレーターを開始するには、「[Using the HoloLens emulator (HoloLens エミュレーターを使用する)](../using-the-hololens-emulator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-127">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="cb2f3-128">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-128">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="cb2f3-129">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="cb2f3-129">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="cb2f3-130">以下のガイドラインは、イマーシブ (VR) ヘッドセットの*開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-130">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="cb2f3-131">この仕様を、[PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる*コンシューマー PC の仕様*について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-131">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="cb2f3-132">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-132">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="cb2f3-133">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-133">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="cb2f3-134">最小</span><span class="sxs-lookup"><span data-stu-id="cb2f3-134">Minimum</span></span></th><th> <span data-ttu-id="cb2f3-135">推奨</span><span class="sxs-lookup"><span data-stu-id="cb2f3-135">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="cb2f3-136">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="cb2f3-136">Processor</span></span></td><td> <span data-ttu-id="cb2f3-137"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="cb2f3-137"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="cb2f3-138"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="cb2f3-138"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-139">GPU</span><span class="sxs-lookup"><span data-stu-id="cb2f3-139">GPU</span></span></td><td> <span data-ttu-id="cb2f3-140"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="cb2f3-140"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="cb2f3-141"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="cb2f3-141"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-142">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="cb2f3-142">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-143">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="cb2f3-143">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-144">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="cb2f3-144">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-145">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="cb2f3-145">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-146">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="cb2f3-146">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-147">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="cb2f3-147">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-148">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="cb2f3-148">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-149">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="cb2f3-149">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-150">メモリ</span><span class="sxs-lookup"><span data-stu-id="cb2f3-150">Memory</span></span></td><td> <span data-ttu-id="cb2f3-151">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="cb2f3-151">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="cb2f3-152">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="cb2f3-152">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-153">記憶域</span><span class="sxs-lookup"><span data-stu-id="cb2f3-153">Storage</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-154">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="cb2f3-154">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-155">USB ポート</span><span class="sxs-lookup"><span data-stu-id="cb2f3-155">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-156">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="cb2f3-156">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-157">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="cb2f3-157">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-158">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="cb2f3-158">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

### <a name="whats-next"></a><span data-ttu-id="cb2f3-159">次の手順</span><span class="sxs-lookup"><span data-stu-id="cb2f3-159">What's next?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cb2f3-160">Unity の体験を開始する</span><span class="sxs-lookup"><span data-stu-id="cb2f3-160">Start your Unity journey</span></span>](../unity-development-overview.md)

# <a name="unreal"></a>[<span data-ttu-id="cb2f3-161">Unreal</span><span class="sxs-lookup"><span data-stu-id="cb2f3-161">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="cb2f3-163">1.最新バージョンをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="cb2f3-163">1. Download the latest version</span></span>

<span data-ttu-id="cb2f3-164">組み込みの HoloLens サポートを最大限に活用するため、[Unreal Engine バージョン 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 以降をインストールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-164">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="cb2f3-165">2.Mixed Reality Toolkit (MRTK) をインポートする</span><span class="sxs-lookup"><span data-stu-id="cb2f3-165">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../images/UX/MRTK_UX_Hero.png)

<span data-ttu-id="cb2f3-167">Mixed Reality Toolkit (MRTK) は、Mixed Reality アプリケーション向けのオープン ソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-167">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="cb2f3-168">MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-168">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="cb2f3-169">このツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-169">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="cb2f3-170"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="cb2f3-170"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="cb2f3-171">**Mixed Reality Toolkit-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="cb2f3-171">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="cb2f3-172">Unreal 用の MRTK を使用しない場合は、すべての対話式操作と動作のスクリプトを開発者が自分で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-172">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="cb2f3-173">その他のツール (省略可能)</span><span class="sxs-lookup"><span data-stu-id="cb2f3-173">Other tools [optional]</span></span>
* <span data-ttu-id="cb2f3-174"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-174"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="cb2f3-175"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-175"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="cb2f3-176">3.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="cb2f3-176">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="cb2f3-177">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-177">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="cb2f3-178">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-178">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="cb2f3-179">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-179">Note that not all tools are supported on older operating systems.</span></span> 

> [!NOTE]
> <span data-ttu-id="cb2f3-180">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-180">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="cb2f3-181">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-181">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="cb2f3-182">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="cb2f3-182">For HoloLens development</span></span>

<span data-ttu-id="cb2f3-183">HoloLens の開発用に開発用 PC を設定するときは、[Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) と <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-183">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="cb2f3-184">[HoloLens エミュレーター](../using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-184">If you plan on using the [HoloLens emulator](../using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="cb2f3-185">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-185">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="cb2f3-186">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="cb2f3-186">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="cb2f3-187">以下のガイドラインは、イマーシブ (VR) ヘッドセットの*開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-187">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="cb2f3-188">この仕様を、[PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる*コンシューマー PC の仕様*について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-188">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="cb2f3-189">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-189">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="cb2f3-190">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-190">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="cb2f3-191">最小</span><span class="sxs-lookup"><span data-stu-id="cb2f3-191">Minimum</span></span></th><th> <span data-ttu-id="cb2f3-192">推奨</span><span class="sxs-lookup"><span data-stu-id="cb2f3-192">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="cb2f3-193">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="cb2f3-193">Processor</span></span></td><td> <span data-ttu-id="cb2f3-194"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="cb2f3-194"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="cb2f3-195"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="cb2f3-195"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-196">GPU</span><span class="sxs-lookup"><span data-stu-id="cb2f3-196">GPU</span></span></td><td> <span data-ttu-id="cb2f3-197"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="cb2f3-197"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="cb2f3-198"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="cb2f3-198"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-199">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="cb2f3-199">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-200">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="cb2f3-200">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-201">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="cb2f3-201">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-202">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="cb2f3-202">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-203">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="cb2f3-203">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-204">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="cb2f3-204">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-205">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="cb2f3-205">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-206">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="cb2f3-206">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-207">メモリ</span><span class="sxs-lookup"><span data-stu-id="cb2f3-207">Memory</span></span></td><td> <span data-ttu-id="cb2f3-208">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="cb2f3-208">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="cb2f3-209">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="cb2f3-209">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-210">記憶域</span><span class="sxs-lookup"><span data-stu-id="cb2f3-210">Storage</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-211">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="cb2f3-211">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-212">USB ポート</span><span class="sxs-lookup"><span data-stu-id="cb2f3-212">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-213">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="cb2f3-213">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-214">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="cb2f3-214">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-215">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="cb2f3-215">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

### <a name="whats-next"></a><span data-ttu-id="cb2f3-216">次の手順</span><span class="sxs-lookup"><span data-stu-id="cb2f3-216">What's next?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cb2f3-217">Unreal の体験を開始する</span><span class="sxs-lookup"><span data-stu-id="cb2f3-217">Start your Unreal journey</span></span>](../unreal-development-overview.md)

# <a name="native-openxr"></a>[<span data-ttu-id="cb2f3-218">ネイティブ (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="cb2f3-218">Native (OpenXR)</span></span>](#tab/native)

 ![ネイティブ アプリ開発](../images/native_logo_banner.png)

<span data-ttu-id="cb2f3-220">ネイティブな OpenXR 開発では、エンジンをダウンロードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-220">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="cb2f3-221">「[OpenXR の概要](../openxr-getting-started.md)」に、開発を開始するために必要なものがすべて記載されています。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-221">You can find everything you need to begin development in the [Getting started with OpenXR](../openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="cb2f3-222">1.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="cb2f3-222">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="cb2f3-223">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-223">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="cb2f3-224">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-224">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="cb2f3-225">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-225">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="cb2f3-226">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="cb2f3-226">For HoloLens development</span></span>

<span data-ttu-id="cb2f3-227">HoloLens の開発用に開発用 PC を設定するときは、<a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-227">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="cb2f3-228">[HoloLens エミュレーター](../using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-228">If you plan on using the [HoloLens emulator](../using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="cb2f3-229">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-229">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="cb2f3-230">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-230">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="cb2f3-231">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-231">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="cb2f3-232">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="cb2f3-232">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="cb2f3-233">以下のガイドラインは、イマーシブ (VR) ヘッドセットの*開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-233">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="cb2f3-234">この仕様を、[PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる*コンシューマー PC の仕様*について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-234">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="cb2f3-235">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-235">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="cb2f3-236">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="cb2f3-236">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="cb2f3-237">最小</span><span class="sxs-lookup"><span data-stu-id="cb2f3-237">Minimum</span></span></th><th> <span data-ttu-id="cb2f3-238">推奨</span><span class="sxs-lookup"><span data-stu-id="cb2f3-238">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="cb2f3-239">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="cb2f3-239">Processor</span></span></td><td> <span data-ttu-id="cb2f3-240"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="cb2f3-240"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="cb2f3-241"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="cb2f3-241"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-242">GPU</span><span class="sxs-lookup"><span data-stu-id="cb2f3-242">GPU</span></span></td><td> <span data-ttu-id="cb2f3-243"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="cb2f3-243"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="cb2f3-244"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="cb2f3-244"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-245">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="cb2f3-245">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-246">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="cb2f3-246">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-247">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="cb2f3-247">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-248">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="cb2f3-248">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-249">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="cb2f3-249">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-250">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="cb2f3-250">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-251">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="cb2f3-251">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-252">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="cb2f3-252">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-253">メモリ</span><span class="sxs-lookup"><span data-stu-id="cb2f3-253">Memory</span></span></td><td> <span data-ttu-id="cb2f3-254">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="cb2f3-254">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="cb2f3-255">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="cb2f3-255">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-256">記憶域</span><span class="sxs-lookup"><span data-stu-id="cb2f3-256">Storage</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-257">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="cb2f3-257">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-258">USB ポート</span><span class="sxs-lookup"><span data-stu-id="cb2f3-258">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-259">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="cb2f3-259">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb2f3-260">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="cb2f3-260">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="cb2f3-261">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="cb2f3-261">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

### <a name="whats-next"></a><span data-ttu-id="cb2f3-262">次の手順</span><span class="sxs-lookup"><span data-stu-id="cb2f3-262">What's next?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cb2f3-263">ネイティブの体験を開始する</span><span class="sxs-lookup"><span data-stu-id="cb2f3-263">Start your Native journey</span></span>](../directx-development-overview.md)


