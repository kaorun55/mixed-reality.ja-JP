---
title: ツールのインストール
description: ここでは Mixed Reality の開発の準備を開始します。 この記事では、HoloLens および Windows Mixed Reality のイマーシブ ヘッドセット開発に推奨される Unity、Visual Studio、その他のツールの最新バージョンが常に反映されています。
author: thetuvix
ms.author: alexturn
ms.date: 3/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: 最新, ツール, はじめに, 基本, unity, visual studio, ツールキット
ms.openlocfilehash: 131d2a91c882fbcd31c4deb76a5ab5c3f97d7d42
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "82137877"
---
# <a name="install-the-tools"></a>ツールのインストール

Microsoft HoloLens および Windows Mixed Reality イマーシブ (VR) ヘッドセット用のアプリケーションを構築するために必要なツールを取得します。 Windows Mixed Reality 開発用の別個の SDK はありません。Windows 10 SDK と一緒に Visual Studio をご使用ください。

Mixed Reality デバイスをお持ちでない場合はどのようにしたらよいでしょうか。 HoloLens なしで Mixed Reality アプリの機能をテストするために、[HoloLens エミュレーター](using-the-hololens-emulator.md)をインストールすることができます。 [Windows Mixed Reality シミュレーター](using-the-windows-mixed-reality-simulator.md)を使用して、イマーシブ ヘッドセット用の Mixed Reality アプリをテストすることもできます。

Mixed Reality アプリの作成を開始する最も簡単な方法として、Unity ゲーム エンジンをインストールすることをお勧めします。 ただし、カスタム エンジンを使用する場合は、DirectX に対してビルドすることもできます。

>[!TIP]
>このページをブックマークに登録して定期的にチェックし、Mixed Reality 開発に推奨される各ツールの最新バージョンを常に最新の状態に保ってください。

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>インストールのチェックリスト


| ツール | 説明 | メモ |
|---------|---------|---------|
| ![Windows ロゴ](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (手動インストールのリンク)</a> | お使いの PC のオペレーティング システムが、Mixed Reality アプリケーションの構築対象プラットフォームと一致するように、Windows 10 の最新バージョンをインストールしてください。 | **Windows 10 のインストール** <br> <ul><li>[設定] の [Windows Update] を利用するか、インストール メディアを作成して (左の列のリンクを使用して)、Windows 10 の最新バージョンをインストールできます。<li>Windows 10 の各リリースで使用可能な最新の Mixed Reality 機能については、[最新のリリース ノート](release-notes-october-2018.md)を参照してください。</ul> [設定] > [更新とセキュリティ] > [開発者向け] から、**PC で開発者モードを有効にします**。 <br><br> **エンタープライズ管理および会社管理の PC の場合の注意事項:** お使いの PC が組織の IT 部門によって管理されている場合、更新するために管理者への連絡が必要な場合があります。 <br><br> **Windows の 'N' バージョン:** Windows Mixed Reality イマーシブ (VR) ヘッドセットは、Windows の 'N' バージョンではサポートされていません。 |
| ![Visual Studio のロゴ](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.2 以降)** (インストールのリンク)</a> | 完全な機能を備えた Windows などの統合開発環境 (IDE) です。 コードの記述、デバッグ、テスト、配置には、Visual Studio を使用します。 | 次のワークロードをインストールします。 <ul><li>**C++ によるデスクトップ開発**</li><li>**ユニバーサル Windows プラットフォーム (UWP) の開発**</li></ul>HoloLens 向けの開発を行う場合は、UWP ワークロード内に次のオプションのコンポーネントがあることを確認してください。<ul><li>**USB デバイスの接続**</li></ul>**Unity に関する注意事項:** 特定の目的のために意図的により新しいバージョンの (LTS 以外の) Unity をインストールしようとしているのでなければ、Visual Studio のインストールの一部として Unity ワークロードをインストールする*のではなく*、下記のように **Unity 2018.4 LTS** ストリームをインストールすることをお勧めします。<br> <br>**注:** Visual Studio 2019 バージョン 16.0 での Mixed Reality アプリのデバッグに関して既知の問題がいくつかあります。  必ず、**Visual Studio 2019 バージョン 16.2 以降**に更新してください。 |
| ![Windows ロゴ](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)** (手動インストールのリンク)</a> | HoloLens 2 で Windows 10 アプリを作成するための最新のヘッダー、ライブラリ、メタデータ、ツールが用意されています。 | HoloLens 2 アプリを構築するには、ビルド 18362 以降の Windows SDK をインストールする必要があります。<br> <br> デスクトップの Windows Mixed Reality ヘッドセットまたは HoloLens (第 1 世代) 用のアプリケーションのみを開発している場合は、Visual Studio 2017 によってインストールされた Windows SDK を使用することができます。 |
| ![Visual Studio のロゴ](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2126826" target="_blank">**HoloLens 2 エミュレーター (2020 年 4 月の更新プログラム)** (インストールのリンク:10.0.18362.1059)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens (第 1 世代) エミュレーター** (インストールのリンク:10.0.17763.134)</a> | エミュレーターを使用すると、物理的な HoloLens を使用せずに、HoloLens 仮想マシン イメージ上でアプリケーションを実行できます。<br> <br> | エミュレーターの使用を開始する方法については、「[Using the HoloLens emulator (HoloLens エミュレーターを使用する)](using-the-hololens-emulator.md)」を参照してください。<br> <br> エミュレーターのインストールを成功させるには、**ご使用のシステムが Hyper-V をサポートしている必要があります**。 詳細については、以下の「システム要件」セクションを参照してください。 <br>|

## <a name="choose-your-engine"></a>エンジンの選択

:::row:::
    :::column:::
        <a href="https://unity3d.com/unity/qa/lts-releases?version=2018.4" target="_blank">![Unity](images/unity_logo.png)<br>**Unity**</a><br>
        通常、Unity LTS (長期サポート) ストリームを新しいプロジェクトを開始するのに最適なバージョンとしてお勧めします。最新の安定した修正プログラムを取得するには最新リビジョンに更新します。<br>
        <br>
        現在は、**Unity 2018.4.x** を使用することをお勧めしています。これは、以下の MRTK v2 に必要な LTS ビルドです。<br>
        <br>
        特定の理由から、異なるバージョンの Unity を使用したいという開発者もいます。 このようなケースのために、Unity では異なるバージョンの side-by-side インストールをサポートしています。<br>
        <br>
        HoloLens 2 または Windows Mixed Reality イマーシブ ヘッドセット向けの Unity 開発を開始するには、「[Unity 開発の概要](unity-development-overview.md)」を参照してください。<br>
        <br>
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">![MRTK](images/final_mrtk-small_logo.png)<br>**Mixed Reality ツールキット (MRTK)** </a><br>
        Unity 用の Mixed Reality Toolkit (MRTK) v2 は、Mixed Reality アプリケーション向けのオープン ソースのクロスプラットフォーム開発キットです。<br>
        <br>
        MRTK v2 は、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。 このプロジェクトは、Mixed Reality アプリケーション作成への参入の障壁を減らし、事態の発展とともにコミュニティに貢献することを目的としています。
    :::column-end:::
    :::column:::
        <a href="https://docs.unrealengine.com//GettingStarted/Installation/index.html" target="_blank">![Unreal](images/Unreal_logo.png)<br>**Unreal**</a><br>
        Unreal Engine 4 は、強力なオープン ソースの作成エンジンで、C++ と Blueprints の両方の Mixed Reality を完全にサポートします。<br>
        <br>
        Unreal Engine 4.24 に対する HoloLens のサポートは、現在ベータ版です。<br>
        <br>
        HoloLens 2 向けの Unreal 開発を開始するには、「[Unreal 開発の概要](unreal-development-overview.md)」を参照してください。
    :::column-end:::
    :::column:::
        ![ネイティブ アプリ開発](images/visualstudio-small_logo.png)<br>
        [**ネイティブ (OpanXR)** ](openxr-getting-started.md)<br>
        OpenXR は Khronos によるオープンなロイヤリティフリーの API 標準で、Mixed Reality 業界全体の多くのベンダーからの広範なデバイスに対してエンジンによるネイティブ アクセスを提供します。  <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> プロジェクトでは、2 つの Visual Studio プロジェクト ファイルにより OpenXR の簡単な例が示されています。1 つは Win32 デスクトップ アプリ、もう 1 つは UWP HoloLens 2 アプリ向けです。<br>
        <br>
        <a href="https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX" target="_blank">**ネイティブ (WinRT)** </a><br>
        <a href="https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX" target="_blank">Windows Mixed Reality ネイティブ アプリ テンプレート</a>には、DirectX とネイティブ API を使用して Mixed Reality アプリの記述を開始するのに必要なものすべてが含まれます。 レンダリング ループ (または "ゲーム ループ")、Direct3D デバイスとコンテキストを管理するための DeviceResources ヘルパー クラス、シンプルなサンプル ホログラム レンダラーが含まれています。 Direct3D 11 と Direct3D 12 で使用できます。<br>
        <br>
        HoloLens 2 または Windows Mixed Reality イマーシブ ヘッドセット向けに WinRT または OpenXR を使用してネイティブ アプリ開発を開始するには、「[ネイティブ開発の概要](directx-development-overview.md)」を参照してください。
    :::column-end:::
:::row-end:::

<br>

## <a name="mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit (MRTK)

Mixed Reality Toolkit は、Microsoft HoloLens、Windows Mixed Reality ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としたコンポーネントや機能を提供します。 このプロジェクトは、Mixed Reality アプリケーション作成への参入の障壁を減らし、事態の発展とともにコミュニティに貢献することを目的としています。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit</a> - Mixed Reality アプリケーションの開発を促進するためのスクリプトとコンポーネントのコレクションです。
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit-Unity</a> - 基本ツールキットのコードを使用し、Unity で簡単に使用できるようにします。
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらと組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Mixed Reality 開発用 PC の設定

Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。 この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。 以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。 

### <a name="for-hololens-development"></a>HoloLens の開発の場合

開発用の PC を HoloLens の開発用に設定するときは、<a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> と <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。 HoloLens エミュレーターを使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。

HoloLens エミュレーターを開始するには、「[Using the HoloLens emulator (HoloLens エミュレーターを使用する)](using-the-hololens-emulator.md)」を参照してください。

HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。

### <a name="for-immersive-vr-headset-development"></a>イマーシブ (VR) ヘッドセット開発の場合

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

## <a name="see-also"></a>関連項目

* [開発の概要](development.md)
* [HoloLens エミュレーターを使用する](using-the-hololens-emulator.md)
* [Windows Mixed Reality シミュレーターを使用する](using-the-windows-mixed-reality-simulator.md)
* [Unity 開発の概要](unity-development-overview.md)
* [Unreal 開発の概要](unreal-development-overview.md)
* [DirectX 開発の概要](directx-development-overview.md)
* [HoloLens エミュレーターのアーカイブ](hololens-emulator-archive.md)
