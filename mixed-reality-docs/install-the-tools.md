---
title: ツールをインストールします。
description: ここからの複合現実の開発の準備を開始します。 この記事では、Unity、Visual Studio は、HoloLens と Windows Mixed Reality イマーシブ ヘッドセットの開発に推奨される他のツールの最新バージョンを常に反映する必要があります。
author: yoyozilla
ms.author: yoyozilla
ms.date: 2/11/2019
ms.topic: article
keywords: 最新の状態、ツール、最初に、基本、unity、visual studio、ツールキット
ms.openlocfilehash: da924d98f6869fadb9736000f666616f1372faa3
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605121"
---
# <a name="install-the-tools"></a>ツールをインストールします。

Microsoft HoloLens と Windows Mixed Reality 没入型 (VR) ヘッドセット向けアプリの構築に必要なツールを取得します。 個別の Windows for Mixed Reality の SDK 開発; はありません。Windows 10 SDK には、Visual Studio を使用します。

複合現実デバイスはありませんか。 インストールすることができます、 [HoloLens (第 1 世代) エミュレーター](using-the-hololens-emulator.md)せず、HoloLens の複合現実アプリの一部の機能をテストします。 使用することも、 [Windows Mixed Reality シミュレーター](using-the-windows-mixed-reality-simulator.md)イマーシブ ヘッドセットの複合現実アプリをテストします。

> [!NOTE]
> HoloLens 2 エミュレーターに固有のガイダンスについて[近日](index.md#news-and-notes)します。

複合現実アプリの作成を開始する最も簡単な方法として、Unity ゲーム エンジンをインストールすることをお勧めします。 ただし、ビルドすることも DirectX に対してカスタム エンジンを使用したい場合、

>[!TIP]
>このページをブックマークして、複合現実の開発をお勧めします。 各ツールの最新バージョンの最新の状態を維持するために定期的に確認してください。

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>インストールのチェックリスト


| ツール | 説明 | メモ |
|---------|---------|---------|
| ![Windows ロゴ](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**<br>(手動インストール リンク)</a> | PC のオペレーティング システムがこれには、複合現実アプリをビルドしているプラットフォームと一致するように、最新バージョンの Windows 10 をインストールします。 | **Windows 10 をインストールします。** <br> <ul><li>設定で、または (左側にあるリンクを使用して) インストール メディアを作成して、Windows Update を使用して Windows 10 の最新バージョンをインストールできます。<li>参照してください[最新のリリース ノート](release-notes-october-2018.md)については、最新の Windows 10 のリリースごとに使用可能な実際の機能を混合します。</ul> **お使いの PC で開発者モードを有効にする**設定 > 更新とセキュリティ > 開発者向け。 <br><br> **エンタープライズおよび会社によって管理された Pc 向けの注記:** によってお使いの PC が管理されている場合、組織の IT 部門では、更新するためにパートナーに連絡する必要があります。 <br><br> **Windows の 'n' バージョン:**'N' のバージョンの Windows では、Windows Mixed Reality 没入型 (VR) ヘッドセットはサポートされていません。 |
| ![Visual Studio のロゴ](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2017**<br>(インストール リンク)</a> | Windows の完全な機能を備えた統合開発環境 (IDE) です。 コードを記述、デバッグ、テスト、およびデプロイには、Visual Studio を使用します。 | **ワークロードをインストールする:** <ul><li>C++ によるデスクトップ開発</li><li>ユニバーサル Windows プラットフォームの開発</li></ul>**Unity に関する注意事項。** 特定の目的で新しい (非 LTS) バージョンの Unity をインストールしたい意図的に限りお勧め*いない*Unity ワークロードを Visual Studio のインストールの一部としてインストールして、代わりに 2018.3 LTS をインストール以下に説明したように Unity のストリーム。<br> <br>**注:** Visual Studio 2019 で現時点での複合現実の開発に関するいくつかの既知の問題があります。  ここでは、Visual Studio 2017 を使用し続けることをお勧めします。 |
| ![Windows ロゴ](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windowsinsiderpreviewSDK" target="_blank">**Windows SDK Insider Preview 18362**<br>(手動インストール リンク)</a> | HoloLens 2 の Windows 10 アプリを構築するためには、最新のヘッダー、ライブラリ、メタデータ、およびツールを提供します。 | HoloLens 2 アプリを構築する必要があります<a href="https://insider.windows.com">Windows Insider になる</a>と Windows SDK Insider Preview ビルド 18362 以降をインストールします。<br> <br> デスクトップの Windows Mixed Reality ヘッドセットまたは HoloLens 用アプリにのみ開発するかどうか (第 1 世代)、Visual Studio 2017 でインストールされている Windows SDK を使用することができます。 |
| ![Visual Studio のロゴ](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens (第 1 世代) エミュレーターおよび Holographic のプロジェクト テンプレート**<br>(インストール リンク。10.0.17763.253)</a> | エミュレーターでは、HoloLens でアプリを実行できます。 (第 1 世代) 物理 HoloLens なしの仮想マシン イメージ。<br> <br> このパッケージには、Visual Studio の holographic の DirectX プロジェクト テンプレートも含まれています。 | 参照してください[HoloLens のエミュレーターを使用して](using-the-hololens-emulator.md)emulator を使用した作業の開始の詳細についてはします。<br> <br> **システムで HYPER-V をサポートする必要があります**エミュレーターのインストールが成功します。 詳細については、以下のシステム要件のセクションを参照してください。 必要な場合は、エミュレーターを使用せずテンプレートのみのインストールを選択できます。<br> <br> HoloLens 2 エミュレーターに固有のガイダンスについては、[近日](index.md#news-and-notes)します。 |
| ![Unity のロゴ](images/unity_logo.png)<br><br><a href="https://unity3d.com/get-unity/download" target="_blank">**Unity 2018.3**<br>(インストール リンク)</a> | Unity ゲーム エンジンは、Windows Mixed Reality 機能の組み込みサポートを備えた、複合現実エクスペリエンスを作成する最も簡単な方法です。 | 通常お勧めします Unity LTS (長期間サポート) のストリームとして、新しいプロジェクトを開始する最適なバージョンを最新の安定した修正プログラムを取得する最新のリビジョンを更新しています。<br> <br> 現在の推奨事項は、使用することです。 **Unity 2018.3.x**MRTK v2、下に必要な、Unity の 2018 LTS はすぐにこれをビルドします。 <br> <br> 一部の開発者は可能性がありますの特定の理由から、異なるバージョンの Unity を使用するとしています。 その場合は、Unity では、異なるバージョンのサイド バイ サイドでインストールをサポートしています。 |
| ![MRTK ロゴ](images/MRTKIcon.jpg)<br><br><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">**Unity for mixed Reality ツールキット (MRTK v2)**</a> | Unity の MRTK v2 には、複合現実のアプリケーション用のオープン ソース クロス プラットフォーム開発キットです。<br><br> MRTK v2 の目的は、Microsoft HoloLens、Windows Mixed Reality 没入型 (VR) ヘッドセットと OpenVR プラットフォームを対象とするアプリケーションの開発を促進します。 プロジェクトの目的は、複合現実のアプリケーションを作成するエントリに障壁や拡張としては、私たちのコミュニティに貢献します。 | 詳細については、MRTK v2 プロジェクトの訪問して<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki" target="_blank">GitHub wiki</a>します。 |


## <a name="mixed-reality-toolkit"></a>Mixed Reality ツールキット

Mixed Reality Toolkit は、コンポーネントと Microsoft HoloLens、Windows Mixed Reality ヘッドセットと OpenVR プラットフォームを対象とするアプリケーションの開発を促進するためのものが機能を提供します。 プロジェクトの目的は、複合現実のアプリケーションを作成しすべての拡大に伴い、コミュニティに貢献するエントリに対する障壁を削減です。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">MixedRealityToolkit</a>
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit Unity</a> - 基本 toolkit からコードを使用し、Unity で使用しやすきます。
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">MixedRealityCompanionKit</a> - コード bits と HoloLens または没入型の (VR) ヘッドセットで直接実行できないコンポーネントが代わりを構築するにペアで、Windows Mixed Reality を対象とします。

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>複合現実の開発用 PC の設定

Windows 10 SDK は、Windows 10 オペレーティング システムに最適です。 この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 にもサポートされます。 以前のオペレーティング システムで、すべてのツールがサポートされていることに注意してください。 

### <a name="for-hololens-development"></a>HoloLens の開発

HoloLens の開発のため開発用 PC を設定する場合をご確認ください両方のシステム要件を満たして<a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a>と<a href="https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs" target="_blank">Visual Studio</a>します。 場合は、HoloLens を使用する (第 1 世代)、PC が満たしているいることを確認する必要なエミュレーター、 [HoloLens のエミュレーターのシステム要件](using-the-hololens-emulator.md#hololens-emulator-system-requirements)も。

HoloLens の概要 (第 1 世代) エミュレーターを参照してください[HoloLens のエミュレーターを使用して](using-the-hololens-emulator.md)します。

> [!NOTE]
> HoloLens 2 エミュレーターに固有のガイダンスについて[近日](index.md#news-and-notes)します。

HoloLens と Windows Mixed Reality の両方の没入型 (VR) ヘッドセットを開発する場合を使用してください、システムの推奨事項と要件以下のセクションでします。

### <a name="for-immersive-vr-headset-development"></a>(VR) ヘッドセットの没入型の開発

>[!NOTE]
>次のガイドラインは、現在の最小および推奨仕様、没入型の (VR) ヘッドセットを*開発用 PC*、定期的に更新される可能性があります。

>[!WARNING]
>これを混同しないでください、[最小 PC ハードウェアの互換性に関するガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)、概要、*コンシューマー PC 仕様*没入型の (VR) ヘッドセット アプリやゲームをターゲットする必要があります。

必要があります、イマーシブ ヘッドセット開発用 PC には、フルサイズの HDMI や USB 3.0 ポートがない場合、[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)ヘッドホンを接続します。

現在は[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)ハイブリッド グラフィックのノートブックでは特に、一部のハードウェア構成にします。

<table>
<tr>
<th></th><th> 最小</th><th> 推奨</th>
</tr><tr>
<td> 処理者</td><td> <b>Notebook:</b>Intel Mobile Core i5 7 世代の CPU、デュアル コア ハイパー スレッディングを<b>デスクトップ。</b>Intel デスクトップ i5 6 世代の CPU、デュアル コア ハイパー スレッディングを<b>または</b>AMD FX4350 4.2 Ghz クアッド コアと同等</td><td> <b>デスクトップ:</b>Intel デスクトップ i7 6 番目の世代 (6 コア)<b>または</b>AMD Ryzen 5 1600 (6 コア、12 個のスレッド)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b>NVIDIA GTX 965 M、AMD RX 460 M (2 GB) 同等またはそれ以上の DX12 対応 GPU<b>デスクトップ。</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2 GB) 同等またはそれ以上 DX12 対応 GPU</td><td><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2 GB) 同等またはそれ以上 DX12 対応 GPU</td>
</tr><tr>
<td> GPU ドライバー WDDM バージョン</td><td colspan="2"> WDDM 2.2 ドライバー</td>
</tr><tr>
<td> 温度のデザインの電源</td><td colspan="2"> 15W 以上</td>
</tr><tr>
<td> グラフィックスのポートを表示します。</td><td colspan="2"> 使用可能なグラフィックス x 1 用のポートを表示する&#160;ヘッドセット (HDMI 1.4 または 60 Hz ヘッドセット、HDMI 2.0 または 90 Hz ヘッドセットのディスプレイ ポート等 1.2 のディスプレイ ポート等 1.2)</td>
</tr><tr>
<td> 画面の解像度</td><td colspan="2"> 解決策:SVGA (800 x 600)、または大きい値のビット深さ:1 ピクセルあたり 32 ビット色</td>
</tr><tr>
<td> メモリ</td><td> 8&#160;GB 以上の RAM</td><td> 16 GB 以上の RAM</td>
</tr><tr>
<td> ストレージ</td><td colspan="2"> &gt;追加の空き領域の 10 GB</td>
</tr><tr>
<td> USB ポート</td><td colspan="2"> ヘッドセット (USB 3.0 Type-A) のポートの使用可能な USB x 1<b>に注意してください。USB は、900mA の最小値を指定する必要があります。</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (for アクセサリ接続)</td>
</tr>
</table>

## <a name="see-also"></a>関連項目

* [開発の概要](development-overview.md)
* [HoloLens のエミュレーターを使用する](using-the-hololens-emulator.md)
* [Windows Mixed Reality シミュレーターの使用](using-the-windows-mixed-reality-simulator.md)
* [Unity 開発の概要](unity-development-overview.md)
* [DirectX の開発の概要](directx-development-overview.md)
* [HoloLens のエミュレーターのアーカイブ](hololens-emulator-archive.md)
