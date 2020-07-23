---
title: Unreal 開発の概要
description: Unreal Engine 4 を使用した Mixed Reality の開発の概要
author: hferrone
ms.author: v-haferr
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, ストリーミング, リモート処理, Mixed Reality, 開発, 入門, 機能, 新しいプロジェクト, エミュレーター, ドキュメント, ガイド, 特徴, ホログラム, ゲームの開発
ms.openlocfilehash: ecf982eb5d8128734c862bac2d8be29c1554edfe
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303623"
---
# <a name="unreal-development-overview"></a>Unreal 開発の概要

<a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="Mixed Reality Docs"> Mixed Reality アプリケーション</a>を使い始めるのは大きなタスクです。 新しい概念、プラットフォーム、最先端のハードウェアは、障壁のように見えるかもしれません。 ただし、Unreal 開発者であれば、ラッキーです。 <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title=" Windows Mixed Reality のドキュメント">Windows Mixed Reality </a> (VR) および <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="HoloLens 2 のドキュメント">HoloLens 2</a> (AR) のサポートが、Unreal Engine の最新の <a href="https://docs.unrealengine.com/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Unreal Engine 4.25 リリース ノート">リリース</a>に含まれるようになりました。 この更新には、次が含まれます。
* Mixed Reality UX Tools プラグインのサポート
* OpenXR のサポート
* デスクトップ アプリからのアプリのリモート処理
* パフォーマンスの向上
* 複合現実キャプチャ
* Azure Spatial Anchors の初期サポート

Unreal 開発が初めての場合は、よくわからないまま開始しないでください。 Unreal の<a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">チュートリアル シリーズ</a>を調べて、Unreal の<a href="https://www.unrealengine.com/marketplace/store" target="_blank">マーケットプレイス</a>と Mixed Reality <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">フォーラム</a>のアセットとサポートをすばやく理解してください。 これらのリソースは、今日の Mixed Reality 市場におけるビルダーや問題ソルバーのコミュニティへのリンクです。

## <a name="mixed-reality-toolkit-for-unreal"></a>Unreal 用 Mixed Reality ツールキット

[Unreal 用 Mixed Reality ツールキット](https://github.com/microsoft/MixedRealityToolkit-Unreal)は、Unreal での開発を高速化するために設計されたコンポーネントのセットです。 各コンポーネントには、イマーシブ エクスペリエンスをセットアップするためのプラグイン、サンプル、およびドキュメントが含まれています。 

[Unreal 用 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) はリリースされる最初のコンポーネントであり、現在 HoloLens 2 でのみサポートされています。 コンポーネント プラグインには、次のような一般的な UX 機能のコード、ブループリント、サンプル アセットが含まれています。
* 入力シミュレーション
* ハンド インタラクション アクター
* 押しボタン コンポーネント
* マニピュレーター コンポーネント
* 動作追従コンポーネント

機能の詳細やプロジェクトの設定に関する情報については、[Unreal 用 の UX ツール](https://github.com/microsoft/MixedReality-UXTools-Unreal) GitHub リポジトリを参照してください。

## <a name="hololens-2-platform-support"></a>HoloLens 2 プラットフォームのサポート
HoloLens 用の Unreal アプリを初めて作成またはデプロイする場合は、Epic Launcher から[補助プラットフォーム サポート ファイルをダウンロードする](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)必要があります。

## <a name="tutorial"></a>チュートリアル

新しいスキルを習得する最良の方法は、両手を使って自分で何かを作成することです。 手始めに、UX Tools プラグインを使用して HoloLens 2 用の[単純なチェス アプリを構築してデプロイする](unreal-uxt-ch1.md)方法を学ぶことをお勧めします。 

エンドツーエンドのチュートリアル シリーズでは、一般的なインタラクティブ UX コンポーネントとシナリオを実際に体験できます。 プロジェクトの設定、シーンへの対話式操作の追加、デバイスまたはエミュレーターへのデプロイを行います。 必要なのは、Windows 10、エミュレーター、および Visual Studio 2019 だけです。

## <a name="debugging"></a>デバッグ

HoloLens 2 上で実行されているアプリを Visual Studio でデバッグするには、[リモート デバイスでインストール済み UWP アプリをデバッグする](https://docs.microsoft.com/visualstudio/debugger/debug-installed-app-package?view=vs-2019#remote)方法に関するページの指示に従ってください。

## <a name="performance"></a>[パフォーマンス]

Mixed Reality 向けの開発には、プラットフォームに依存するパフォーマンス チェックポイントが含まれます。 安定した応答性の高いホログラムを表示するには、HoloLens 2 アプリを 1 秒あたり 60 フレームで実行する必要があります。 さいわい、Unreal アプリケーションでこれを実現するための[パフォーマンスの推奨事項](performance-recommendations-for-unreal.md)を提供しています。

## <a name="guides-to-specific-features"></a>特定の機能のガイド

このチュートリアル シリーズで取り上げられていない Mixed Reality 開発の主要な機能がいくつかあります。 詳細と実際の適用例については、次のガイドをご覧ください。 
* [視線追跡](unreal-gaze-input.md)
* [ハンド トラッキング](unreal-hand-tracking.md)
* [HoloLens カメラ](unreal-hololens-camera.md)
* [空間アンカー](unreal-spatial-anchors.md)
* [空間マッピング](unreal-spatial-mapping.md)
* [空間オーディオ](unreal-spatial-audio.md)
* [ストリーミング](unreal-streaming.md)
* [音声入力](unreal-voice-input.md)
* [QR コード](unreal-qr-codes.md)
* [パフォーマンスの推奨事項](performance-recommendations-for-unreal.md)

## <a name="supported-features"></a>サポートされている機能

| HoloLens 2 の機能 | サポートする最も古い Unreal Engine のバージョン |
| ----------- | ----------- |
| ARM64 のサポート | 4.23 |
| PC からのストリーミング | 4.23 |
| 空間マッピング | 4.23 |
| 手と関節の追跡 | 4.23 |
| 視線追跡 | 4.23 |
| 音声入力 | 4.23 |
| 空間アンカー | 4.23 |
| カメラへのアクセス | 4.23 |
| QR コード | 4.23 |
| 空間オーディオ | 4.23 |
| ストリーミング用の観戦スクリーンのサポート | 4.24 |
| ストリーミングに対する Planar LSR | 4.24 |
| サンプル アプリ ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) および [Mission AR](https://docs.unrealengine.com/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| モバイル マルチビュー: パフォーマンス ヒット 60 fps | 4.25 |
| 3 番目のカメラのレンダリング | 4.25 |
| パッケージ化されたデスクトップ アプリからのストリーミング | 4.25.1 |
| Azure Spatial Anchors for HoloLens 2 (ベータ版) | 4.25 |
| OpenXR のサポート (ベータ版) | 4.25 |
| UX Tools のサポート (0.8) | 4.25 |
| 開発者向けドキュメントおよびチュートリアル | 4.25 |

## <a name="see-also"></a>関連項目
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">ストリーミング、エミュレーターとデバイスへのデプロイに関する Unreal ドキュメント</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">モバイル デバイスのパフォーマンス ガイドライン (Unreal)</a>
