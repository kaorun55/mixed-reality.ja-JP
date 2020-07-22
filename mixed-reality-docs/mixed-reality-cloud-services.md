---
layout: LandingPage
title: 複合現実クラウド サービス
description: Mixed Reality クラウド サービスのリソース。
author: hferrone
ms.author: v-haferr
ms.date: 06/5/2020
ms.topic: overview
ms.localizationpriority: high
keywords: Mixed Reality, 開発する, 開発, HoloLens, クラウド サービス
ms.openlocfilehash: 80b0b802222684c1219987b197e4219eca8bfc56
ms.sourcegitcommit: 8daefb763d1f23fe02b95b766b00b373f04c5c2d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2020
ms.locfileid: "86451388"
---
# <a name="cloud-services"></a>クラウド サービス

## <a name="overview"></a>概要

**Azure Remote Rendering** や **Azure Spatial Anchors** などの Mixed Reality クラウド サービスを使用すると、開発者はさまざまなプラットフォームで魅力的なイマーシブ エクスペリエンスを構築することができます。 これらのサービスを使用すると、3D トレーニング、設備の予測メンテナンス、デザイン レビュー用のアプリケーションを作成する際、プロジェクトに空間認識を統合でき、このすべてをユーザーの環境のコンテキストで行うことができます。

さらに、Mixed Reality には分類されない既存のプロジェクトに簡単に追加できる他の Azure サービスがあります。 Unity 向けの開発を行っている方を対象に、作業の開始に役立つ幅広い[チュートリアル](#standalone-services)をこのページの下部にご用意しています。

## <a name="mixed-reality-services"></a>複合現実サービス

### <a name="azure-remote-rendering"></a>Azure Remote Rendering
[Azure Remote Rendering](https://docs.microsoft.com/azure/remote-rendering) (ARR) は、非常に複雑な 3D モデルをリアル タイムでレンダリングするためのサービスです。 ARR は現在パブリック プレビューの段階です。 HoloLens 2 または Windows デスクトップ PC を対象とした Unity またはネイティブ C++ のプロジェクトにこれを追加できます。

![Unity ショーケース アプリでの Azure Remote Rendering の例](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors
[Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors) (ASA) は、空間認識 Mixed Reality アプリケーションを構築するための、クロスプラットフォームのサービスです。 Azure Spatial Anchors を使用すると、複数デバイス間でのホログラフィック コンテンツのマッピング、保持、共有を、実世界のスケールで実現できます。 

![Azure Spatial Anchors の例](images/persistence.gif)

このサービスは多くの環境で開発でき、デバイスとプラットフォームの大規模なグループにデプロイできます。 そのため、利用できるプラットフォームの一覧には次のように多くのものが含まれます。
* Unity for HoloLens
* Unity for iOS
* Unity for Android
* ネイティブ iOS
* ネイティブ Android
* HoloLens 向け C++/WinRT および DirectX
* Xamarin for iOS
* Xamarin for Android

## <a name="standalone-services"></a>スタンドアロン サービス
次に示すスタンドアロン サービスは Mixed Reality には該当しませんが、さまざまな開発の状況で役に立つ可能性があります。 Unity を使用して開発している場合は、これらの各サービスを新規または既存のプロジェクトに統合することができます。

### <a name="device-support"></a>デバイス サポート
<table>
    <tr>
        <td><strong>Azure クラウド サービス</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td><a href="mr-azure-301.md">言語翻訳</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-302.md">Computer Vision</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-302b.md">Custom Vision</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-303.md">クロスデバイス通知</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-304.md">顔認識</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-305.md">Functions と Storage</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-306.md">ビデオのストリーム配信</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-307.md">Machine Learning</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-308.md">Functions と Storage</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-309.md">Application Insights</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-310.md">物体検出</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-312.md">ボットの統合</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>