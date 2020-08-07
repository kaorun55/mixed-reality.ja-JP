# <a name="unity"></a>[Unity](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a>1.最新バージョンをダウンロードする

新しいプロジェクトを開始する際に使用する最適なバージョンとして、[Unity LTS (長期サポート)](https://unity3d.com/unity/qa/lts-releases) ストリームをお勧めします。最新の安定した修正プログラムを取得するには最新リビジョンに更新します。 
* 現在は、**Unity 2019** を使用することをお勧めしています。これは、以下の MRTK v2 に必要な LTS ビルドです。
* 特定の理由から別のバージョンの Unity を使用する必要がある場合、Unity では異なるバージョンの side-by-side インストールをサポートしています。

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2.Mixed Reality Toolkit (MRTK) をインポートする
![MRTK](../images/UX/MRTK_UX_Hero.png)

[Mixed Reality Toolkit](../mrtk-getting-started.md) (MRTK) は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。 MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。 このツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)<br>**Mixed Reality Toolkit-Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Unity 用の MRTK を使用しない場合は、すべての対話式操作と動作のスクリプトを開発者が自分で作成する必要があります。

#### <a name="other-tools-optional"></a>その他のツール (省略可能)
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3.Mixed Reality 開発用 PC を設定する

Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。 この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。 以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。 

> [!NOTE]
> HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。 必要に応じて、以下の要件を満たしていることをご確認ください。

#### <a name="for-hololens-development"></a>HoloLens の開発の場合

開発用の PC を HoloLens の開発用に設定するときは、<a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> と <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。 [HoloLens エミュレーター](../using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。

HoloLens エミュレーターを開始するには、「[Using the HoloLens emulator (HoloLens エミュレーターを使用する)](../using-the-hololens-emulator.md)」を参照してください。

HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。

#### <a name="immersive-vr-headset-requirements"></a>イマーシブ (VR) ヘッドセットの要件

>[!NOTE]
>以下のガイドラインは、イマーシブ (VR) ヘッドセットの*開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。

>[!WARNING]
>この仕様を、[PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる*コンシューマー PC の仕様*について説明するものです。

イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。

一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。

<table>
<tr>
<th></th><th> 最小</th><th> 推奨</th>
</tr><tr>
<td> プロセッサ</td><td> <b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</td><td> <b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</td>
</tr><tr>
<td> GPU</td><td> <b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</td><td><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</td>
</tr><tr>
<td> GPU ドライバー WDDM バージョン</td><td colspan="2"> WDDM 2.2 ドライバー</td>
</tr><tr>
<td> 熱設計電力</td><td colspan="2"> 15 W 以上</td>
</tr><tr>
<td> グラフィックス表示ポート</td><td colspan="2"> ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</td>
</tr><tr>
<td> 画面の解像度</td><td colspan="2"> 解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</td>
</tr><tr>
<td> メモリ</td><td> 8&#160;GB 以上の RAM</td><td> 16 GB 以上の RAM</td>
</tr><tr>
<td> 記憶域</td><td colspan="2"> &gt;10 GB の追加の空き領域</td>
</tr><tr>
<td> USB ポート</td><td colspan="2"> ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (アクセサリ接続用)</td>
</tr>
</table>

### <a name="whats-next"></a>次の手順

> [!div class="nextstepaction"]
> [Unity の体験を開始する](../unity-development-overview.md)

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1.最新バージョンをダウンロードする

組み込みの HoloLens サポートを最大限に活用するため、[Unreal Engine バージョン 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 以降をインストールすることをお勧めします。

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2.Mixed Reality Toolkit (MRTK) をインポートする
![MRTK](../images/UX/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) は、Mixed Reality アプリケーション向けのオープン ソースのクロスプラットフォーム開発キットです。 MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。 このツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Unreal 用の MRTK を使用しない場合は、すべての対話式操作と動作のスクリプトを開発者が自分で作成する必要があります。

#### <a name="other-tools-optional"></a>その他のツール (省略可能)
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3.Mixed Reality 開発用 PC を設定する

Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。 この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。 以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。 

> [!NOTE]
> HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。 必要に応じて、以下の要件を満たしていることをご確認ください。

#### <a name="for-hololens-development"></a>HoloLens の開発の場合

HoloLens の開発用に開発用 PC を設定するときは、[Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) と <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。 [HoloLens エミュレーター](../using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。

HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。

#### <a name="immersive-vr-headset-requirements"></a>イマーシブ (VR) ヘッドセットの要件

>[!NOTE]
>以下のガイドラインは、イマーシブ (VR) ヘッドセットの*開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。

>[!WARNING]
>この仕様を、[PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる*コンシューマー PC の仕様*について説明するものです。

イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。

一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。

<table>
<tr>
<th></th><th> 最小</th><th> 推奨</th>
</tr><tr>
<td> プロセッサ</td><td> <b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</td><td> <b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</td>
</tr><tr>
<td> GPU</td><td> <b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</td><td><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</td>
</tr><tr>
<td> GPU ドライバー WDDM バージョン</td><td colspan="2"> WDDM 2.2 ドライバー</td>
</tr><tr>
<td> 熱設計電力</td><td colspan="2"> 15 W 以上</td>
</tr><tr>
<td> グラフィックス表示ポート</td><td colspan="2"> ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</td>
</tr><tr>
<td> 画面の解像度</td><td colspan="2"> 解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</td>
</tr><tr>
<td> メモリ</td><td> 8&#160;GB 以上の RAM</td><td> 16 GB 以上の RAM</td>
</tr><tr>
<td> 記憶域</td><td colspan="2"> &gt;10 GB の追加の空き領域</td>
</tr><tr>
<td> USB ポート</td><td colspan="2"> ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (アクセサリ接続用)</td>
</tr>
</table>

### <a name="whats-next"></a>次の手順

> [!div class="nextstepaction"]
> [Unreal の体験を開始する](../unreal-development-overview.md)

# <a name="native-openxr"></a>[ネイティブ (OpenXR)](#tab/native)

 ![ネイティブ アプリ開発](../images/native_logo_banner.png)

ネイティブな OpenXR 開発では、エンジンをダウンロードする必要はありません。 「[OpenXR の概要](../openxr-getting-started.md)」に、開発を開始するために必要なものがすべて記載されています。

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1.Mixed Reality 開発用 PC を設定する

Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。 この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。 以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。

#### <a name="for-hololens-development"></a>HoloLens の開発の場合

HoloLens の開発用に開発用 PC を設定するときは、<a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> のシステム要件を満たしていることをご確認ください。 [HoloLens エミュレーター](../using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。

HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。

> [!NOTE]
> HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。 必要に応じて、以下の要件を満たしていることをご確認ください。

#### <a name="immersive-vr-headset-requirements"></a>イマーシブ (VR) ヘッドセットの要件

>[!NOTE]
>以下のガイドラインは、イマーシブ (VR) ヘッドセットの*開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。

>[!WARNING]
>この仕様を、[PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる*コンシューマー PC の仕様*について説明するものです。

イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。

一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。

<table>
<tr>
<th></th><th> 最小</th><th> 推奨</th>
</tr><tr>
<td> プロセッサ</td><td> <b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</td><td> <b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</td>
</tr><tr>
<td> GPU</td><td> <b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</td><td><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</td>
</tr><tr>
<td> GPU ドライバー WDDM バージョン</td><td colspan="2"> WDDM 2.2 ドライバー</td>
</tr><tr>
<td> 熱設計電力</td><td colspan="2"> 15 W 以上</td>
</tr><tr>
<td> グラフィックス表示ポート</td><td colspan="2"> ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</td>
</tr><tr>
<td> 画面の解像度</td><td colspan="2"> 解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</td>
</tr><tr>
<td> メモリ</td><td> 8&#160;GB 以上の RAM</td><td> 16 GB 以上の RAM</td>
</tr><tr>
<td> 記憶域</td><td colspan="2"> &gt;10 GB の追加の空き領域</td>
</tr><tr>
<td> USB ポート</td><td colspan="2"> ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (アクセサリ接続用)</td>
</tr>
</table>

### <a name="whats-next"></a>次の手順

> [!div class="nextstepaction"]
> [ネイティブの体験を開始する](../directx-development-overview.md)


