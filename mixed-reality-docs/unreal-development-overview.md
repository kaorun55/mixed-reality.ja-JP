---
title: Unreal 開発の概要
description: Unreal Engine 4 を使用した Mixed Reality の開発の概要
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, ストリーミング, リモート処理, Mixed Reality, 開発, 入門, 機能, 新しいプロジェクト, エミュレーター, ドキュメント, ガイド, 特徴, ホログラム
ms.openlocfilehash: 08ba760acc1a35d8f47de6a7bf6cbc020c8aca3f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851566"
---
# <a name="unreal-development-overview"></a>Unreal 開発の概要

Unreal Engine 4 は、Windows Mixed Reality (VR) と HoloLens 2 (AR) の両方のデバイスの開発を完全にサポートするようになりました。 Unreal での開発を初めて行う場合は、「<a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">UE4 をはじめよう</a>」ページが非常に参考になります。 資産が必要であれば、Unreal には包括的な<a href="https://www.unrealengine.com/marketplace//store" target="_blank">マーケットプレース</a>があります。 

Unreal 開発の基本を理解したら、次のセクションのチュートリアルを参照して、HoloLens でアプリをビルドおよび実行する方法を確認してください。 必ず <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal 複合現実フォーラム</a>にアクセスして、Unreal で複合現実アプリをビルドしているコミュニティに参加してください。 このコミュニティは、直面した問題の解決策を見つけるのに最適な場所です。

## <a name="tutorial"></a>チュートリアル

Microsoft のエンドツーエンドのチュートリアルに従って、HoloLens 2 用の[簡単なチェス アプリをビルドしてデプロイする](unreal-uxt-ch1.md)方法について説明します。 このチュートリアルでは、UX Tools プラグインを使用して、ボタンやマニピュレーターなどの対話型 UX コンポーネントにより、アプリの開発を促進します。 UX Tools プラグインの詳細については、MRTK に関する次のセクションを参照してください。 

## <a name="mixed-reality-toolkit-for-unreal"></a>Unreal 用 Mixed Reality ツールキット

[Unreal 用 Mixed Reality ツールキット](https://github.com/microsoft/MixedRealityToolkit-Unreal)は、Unreal Engine を使用して Mixed Reality アプリケーションの開発を促進することを目的に設計された、プラグイン形式のコンポーネント、サンプル、ドキュメントのセットです。 このツールキットの一部として最初にリリースされたコンポーネントは、[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) です。これは、HoloLens 2 プロジェクトに追加できるプラグインで、HoloLens 2 アプリケーション用の UX 機能を提供します。 Mixed Reality ツールキットと UX Tools for Unreal のドキュメントは、それぞれの GitHub リポジトリにあります。 

## <a name="performance"></a>[パフォーマンス]

安定した応答性の高いホログラムを表示するには、HoloLens 2 アプリを 1 秒あたり 60 フレームで実行する必要があります。 アプリでこれを実現するには、「[Unreal のパフォーマンスに関する推奨事項](performance-recommendations-for-unreal.md)」に従うことを強くおすすめします。 

## <a name="guides-to-specific-features"></a>特定の機能のガイド

Unreal の特定の機能を使用する方法については、以下のガイドを参照してください。 
* [ハンド トラッキング](unreal-hand-tracking.md)
* [視線追跡](unreal-gaze-input.md)
* [空間マッピング](unreal-spatial-mapping.md)
* [空間アンカー](unreal-spatial-anchors.md)
* [音声入力](unreal-voice-input.md)
* [HoloLens カメラ](unreal-hololens-camera.md)
* [QR コード](unreal-qr-codes.md)

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
| サンプル アプリ ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) および [Mission AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| モバイル マルチビュー: パフォーマンス ヒット 60 fps | 4.25 |
| 3 番目のカメラのレンダリング | 4.25 |
| パッケージ化されたデスクトップ アプリからのストリーミング | 4.25 |
| Azure Spatial Anchors for HoloLens 2 (ベータ版) | 4.25 |
| OpenXR のサポート (ベータ版) | 4.25 |
| UX Tools のサポート (0.8) | 4.25 |
| 開発者向けドキュメントおよびチュートリアル | 4.25 |

## <a name="see-also"></a>関連項目
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">ストリーミング、エミュレーターとデバイスへのデプロイに関する Unreal ドキュメント</a>
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">モバイル デバイスのパフォーマンス ガイドライン (Unreal)</a>
