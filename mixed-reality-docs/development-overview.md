---
title: 開発の概要
description: この記事では、Windows Mixed Reality アプリを開発するための基本的な構成要素について説明します。
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: はじめに, 基本, HoloLens, HoloLens 2, イマーシブヘッドセット, unity, visual studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873976"
---
# <a name="development-overview"></a>開発の概要

混合 reality アプリは、さまざまな開発者テクノロジを使用して開発できます。  HoloLens は、[ユニバーサル Windows プラットフォーム](https://dev.windows.com/getstarted)でビルドされたアプリを実行します。  イマーシブヘッドセットは、Win32 アプリケーションと同様に、ユニバーサル Windows プラットフォームアプリを実行します。
Unity などのミドルウェアツールを使い慣れていれば、今すぐに mixed reality エクスペリエンスの構築を始めることができます。  オープンソースの[Mixed Reality ツールキット](install-the-tools.md)を利用して、すぐに使い始めることができます。
<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>などの<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Mixed reality サービス</a>には、さまざまなクロスプラットフォーム開発者テクノロジに統合できる sdk が用意されています。

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>Mixed Reality 開発の基礎

[Mixed Reality](mixed-reality.md) エクスペリエンスは、Windows の新しい環境認識機能によって実現されています。 開発者は、これを使って現実世界に[ホログラム](hologram.md)を配置できます。また、ユーザーが実際に歩くことで、デジタル世界を動き回ることができるようにもなります。 

次に示すのは、Mixed Reality 開発のコア構成要素です。

<table>
<tr>
<th>入力</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> <a href="gaze.md">頭の視線入力</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">目の視線入力</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> ハンド/<a href="gestures.md">ジェスチャ</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">音声</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">ゲームパッド</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">モーション コントローラー</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> 認識と空間機能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">ワールド座標</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">立体音響</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">空間マッピング</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



[HoloLens](hololens-hardware-details.md) の基本的な操作モデルは、[視線入力](gaze.md)、[ジェスチャ](gestures.md)、および[音声](voice-input.md)です。これらは、*GGV* と呼ばれることもあります。 [Windows Mixed Reality イマーシブ ヘッドセット](immersive-headset-hardware-details.md)も視線入力と音声を使用しますが、ジェスチャは[モーション コントローラー](motion-controllers.md)に置き換わっています。


Windows ベースのすべての mixed reality デバイスは、Windows で使用できる入力エコシステム (マウス、キーボード、ゲームパッドなど) の恩恵を受けます。 HoloLens では、Bluetooth 経由で[ハードウェア アクセサリ](hardware-accessories.md)を接続します。 イマーシブ ヘッドセットでは、Bluetooth、USB、およびその他のサポートされているプロトコルを使用してアクセサリーをホスト PC に接続します。

[座標](coordinate-systems.md)、[立体音響](spatial-sound.md)、および[空間マッピング](spatial-mapping.md)などの環境認識機能は、Mixed Reality に必要な機能を提供します。 空間マッピングは HoloLens に固有で、ホログラムがユーザーや周辺の物理世界と相互作用できるようにしています。 座標系は、ユーザーの移動がデジタル世界に影響するようにしています。

[ホログラム](hologram.md)は、 [holographic レンダリング](rendering.md)に依存するライトとサウンドで構成されています。 [Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md) (「シェル」とも呼ばれます) で説明されているように、配置と永続化のエクスペリエンスを理解することは、ユーザー エクスペリエンスに根ざす優れた方法です。

## <a name="tools-for-developing-for-mixed-reality"></a>Mixed Reality 用の開発ツール

使用するツールは、構築する[アプリのスタイル](app-views.md)によって異なります。
* [2D 表示を使用するアプリ](building-2d-apps.md)では、Windows Phone、PC、タブレットなどの環境に最適なユニバーサル Windows プラットフォーム アプリを構築するツールを活用します。 これらのアプリは、Windows Mixed Reality ホームで 2D のプロジェクションとしてのエクスペリエンスを提供し、(スマート フォンと PC を含む) 複数の種類のデバイスで動作します。
* イマーシブおよびホログラフィック アプリには、Windows Mixed Reality API を活用するために設計されたツールが必要です。 Mixed Reality アプリの構築には、[Unity の使用をお勧めします](unity-development-overview.md)。 独自エンジンの構築に関心がある開発者は、[DirectX などの Windows API を使用します](directx-development-overview.md)。

以下のツールは、構築しているアプリの種類には関係なく、アプリ開発エクスペリエンスを向上させます。
* [Visual Studio と Windows SDK](using-visual-studio.md)
* [Windows Device Portal](using-the-windows-device-portal.md)
* [HoloLens エミュレーター](using-the-hololens-emulator.md)(HoloLens 2 emulator は近日公開予定)
* [Windows Mixed Reality シミュレーター](using-the-windows-mixed-reality-simulator.md)
* [アプリの品質基準](app-quality-criteria.md)

## <a name="see-also"></a>関連項目
* [ツールのインストール](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Mixed reality サービス</a>
* [Mixed Reality チュートリアル](tutorials.md)
* [オープンソースプロジェクト](open-source-projects.md)
* [MR の基本 100:Unity の概要](holograms-100.md)
* [Windows Mixed Reality の PC ハードウェアの最小互換性ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Windows ストアへのアプリの送信](submitting-an-app-to-the-microsoft-store.md)
