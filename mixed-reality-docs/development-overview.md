---
title: 開発の概要
description: この記事では、Windows Mixed Reality アプリの開発の基本的な構成要素について説明します。
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: 取得未開始状態、基本、HoloLens、HoloLens 2、イマーシブ ヘッドセット、unity、visual studio
ms.openlocfilehash: 1d23e458477cc23252ccd4c44f67c400aa356965
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605111"
---
# <a name="development-overview"></a>開発の概要

複合現実アプリは、さまざまな開発者向けテクノロジを使用して開発できます。  HoloLens で構築されたアプリの実行、[ユニバーサル Windows プラットフォーム](https://dev.windows.com/getstarted)します。  イマーシブ ヘッドセットは、Win32 アプリケーションだけでなく、ユニバーサル Windows プラットフォーム アプリを実行します。
慣れる過程 Unity などのミドルウェアのツールで、複合現実に今日が発生したビルドを開始できます。  オープン ソースを利用して[Mixed Reality Toolkit](install-the-tools.md)をすぐに開始します。
<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">実際のサービスを混在</a>など<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>、さまざまなクロス プラットフォームの開発者テクノロジにも組み込めます Sdk があります。

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>複合現実の開発の基礎

[複合現実](mixed-reality.md)環境について、Windows の新機能によってエクスペリエンスが有効になっています。 これらを配置する開発者が有効にする、[ホログラム](hologram.md)現実の世界では文字どおりウォークすることによって、デジタルの世界を移動するユーザーを許可するとします。 

複合現実の開発用のコア ビルディング ブロックを次に示します。

<table>
<tr>
<th>入力</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> <a href="gaze.md">Head 視線入力</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">目の視線入力</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> ハンド/<a href="gestures.md">ジェスチャ</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">音声</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Gamepad</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">アニメーション コント ローラー</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> 概念と空間機能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">ワールド座標</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">空間のサウンド</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">空間マッピング</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



基本的な対話モデル[HoloLens](hololens-hardware-details.md)は[視線](gaze.md)、[ジェスチャ](gestures.md)、および[音声](voice-input.md)も呼ばれる*GGV*. [Windows Mixed Reality イマーシブ ヘッドセット](immersive-headset-hardware-details.md)も使用注視し、音声がスワップ[コント ローラーのモーション](motion-controllers.md)ジェスチャ。


複合現実の Windows ベースのすべてのデバイスは、使用可能な入力のエコシステムなど、マウス、キーボード、ゲームパッド、および Windows を享受できます。 HoloLens で[ハードウェア アクセサリ](hardware-accessories.md)Bluetooth 経由で接続しています。 イマーシブ ヘッドセットは、[アクセサリ] は、Bluetooth、USB、およびその他のサポートされているプロトコルを使用してホスト PC に接続します。

などの環境について機能[座標](coordinate-systems.md)、[空間サウンド](spatial-sound.md)、および[空間マッピング](spatial-mapping.md)現実の混在するために必要な機能を提供します。 空間マッピングは、HoloLens に固有ホログラム ユーザーおよび物理世界の両方と対話できるようにします。 座標系は、デジタルの世界での移動に影響を与えるユーザーの移動を許可します。

[ホログラム](hologram.md)光とサウンド、依存する成ります[holographic レンダリング](rendering.md)します。 説明するように配置し、永続化のエクスペリエンスを理解、 [Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)("shell"とも呼ばれます) は優れた方法な用途に自分で、ユーザー エクスペリエンスにします。

## <a name="tools-for-developing-for-mixed-reality"></a>複合現実向けの開発用ツール

使用するツールによって異なりますが、[スタイルのアプリ](app-views.md)をビルドします。
* [2D のビューを使用したアプリ](building-2d-apps.md)Windows Phone、PC、タブレットなどの環境に最適なユニバーサル Windows プラットフォーム アプリの構築のツールを活用します。 これらのアプリは、home、Windows Mixed Reality に 2D のプロジェクションとして経験を積んだ (スマート フォンと PC を含む) 複数のデバイスの種類の間で作業できます。
* 没入型および holographic アプリには、Windows の混合実際には Api を活用するために設計されたツールが必要があります。 私たち[Unity を使用すること勧め](unity-development-overview.md)複合現実アプリを構築します。 独自のエンジンの構築に関心がある開発者は[DirectX およびその他の Windows Api を使用して、](directx-development-overview.md)します。

で構築しているアプリの種類に関係なく、これらのツールは、アプリの開発エクスペリエンスを容易になります。
* [Visual Studio と Windows SDK](using-visual-studio.md)
* [Windows Device Portal](using-the-windows-device-portal.md)
* [HoloLens のエミュレーター](using-the-hololens-emulator.md) (HoloLens 2 エミュレーターが近日公開予定)
* [Windows Mixed Reality シミュレーター](using-the-windows-mixed-reality-simulator.md)
* [アプリの品質基準](app-quality-criteria.md)

## <a name="see-also"></a>関連項目
* [ツールをインストールします。](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">複合現実のサービス</a>
* [Mixed Reality チュートリアル](academy.md)
* [オープン ソース プロジェクト](open-source-projects.md)
* [MR 基礎 100:Unity の概要](holograms-100.md)
* [Windows Mixed Reality 最小 PC ハードウェアの互換性ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Windows ストア アプリの提出](submitting-an-app-to-the-microsoft-store.md)
