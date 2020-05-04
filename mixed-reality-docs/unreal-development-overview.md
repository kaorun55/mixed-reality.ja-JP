---
title: Unreal 開発の概要
description: Unreal で複合現実アプリのビルドを開始します。
author: sw5813
ms.author: suwu
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4、HoloLens, HoloLens 2, ベータ, ストリーミング, リモート処理, 複合現実, 開発, 使用の開始, 新しいプロジェクト, エミュレーター, ドキュメント
ms.openlocfilehash: 96b0259e4ac567389f999d3a453fb68bb848b266
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "74491170"
---
# <a name="unreal-development-overview"></a>Unreal 開発の概要

Unreal Engine 4 の複合現実のサポートがベータ版になりました。 Unreal での開発を初めて行う場合は、「<a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">UE4 をはじめよう</a>」ページが非常に参考になります。 資産が必要であれば、Unreal には包括的な<a href="https://www.unrealengine.com/marketplace//store" target="_blank">マーケットプレース</a>があります。 

Unreal Engine 4 の基本を理解したら、Unreal Engine ドキュメント サイトの「<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens 開発</a>」ページにアクセスして、HoloLens でアプリをビルドして実行する方法を確認できます。 <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal 複合現実フォーラム</a>にアクセスして、Unreal で複合現実アプリをビルドしているコミュニティに参加してください。 それは、発生する可能性のある問題の解決策を見つけるのに最適な場所です。

## <a name="installing-the-prerequisites"></a>必要条件のインストール

Unreal で HoloLens 2 アプリのビルドを 開始するには、[HoloLens 2 エミュレーター](using-the-hololens-emulator.md)または HoloLens ヘッドセットが必要です。 さらに、「<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">HoloLens 2 前提条件</a>」に記載されているワークロードとコンポーネントを備えた最新バージョンの Visual Studio をインストールする必要があります。

## <a name="building-and-running-your-unreal-app"></a>Unreal アプリのビルドと実行

最初に、<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">アプリを HoloLens 2 用にパッケージ化</a>します。 次に、パッケージのデプロイ先を選択します。
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">HoloLens 2 エミュレーターにデプロイする</a>
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">HoloLens 2 ヘッドセットにデプロイする</a>

## <a name="streaming-your-app-to-a-headset-via-the-holographic-remoting-player"></a>ホログラフィック リモート プレーヤー経由のヘッドセットへのアプリのストリーミング

デスクトップから HoloLens ヘッドセット上の Holographic Remoting Player アプリへのアプリのストリーミングには、2 つの大きなメリットがあります。 
* 開発が高速化されます。このため、変更を加えるたびにアプリを再パッケージ化してアップロードする必要はありません。
* デスクトップのパワーが活用されます。このため、ヘッドセットで利用できるコンピューターによる制限を受けずに、デスクトップの GPU で許可されるだけの数のポリゴンをレンダリングできます。

ストリーミングの使用を開始するには、「<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2 ストリーミングのクイック スタート</a>[]()」をご確認ください。

## <a name="see-also"></a>関連項目
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">モバイル デバイスのパフォーマンス ガイドライン (Unreal)</a>
