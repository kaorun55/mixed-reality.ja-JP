---
title: Holographic DirectX アプリでの XAML の使用
description: DirectX アプリでの 2D XAML ビューとイマーシブビューの切り替えの影響と、XAML ビューとイマーシブビューの両方を効率的に使用する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: windows mixed reality, UWP, アプリビュー管理, xaml, キーボード, チュートリアル, DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548702"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Holographic DirectX アプリでの XAML の使用

このトピックでは、DirectX アプリでの[2D XAML ビューとイマーシブビュー](app-views.md)の切り替えの影響と、xaml ビューとイマーシブビューの両方を効率的に使用する方法について説明します。

## <a name="xaml-view-switching-overview"></a>XAML ビューの切り替えの概要

HoloLens では、一般に 2D XAML ビューを表示できるイマーシブアプリでは、最初に XAML ビューを初期化し、そこからすぐにイマーシブビューに切り替える必要があります。 これは、アプリが何かを実行する前に XAML が読み込まれることを意味します。 結果として、起動時間がわずかに増加し、XAML はバックグラウンドでアプリケーションプロセスのメモリ領域を占有し続けます。起動時の遅延とメモリの使用量は、ネイティブビューに切り替える前に、アプリが XAML で何を実行しているかによって異なります。 XAML の最初のコードで何も実行しない場合は、まず、[イマーシブビューを開始] を除き、影響を軽微にする必要があります。 また、holographic のレンダリングは、イマーシブビューに直接行われるため、そのレンダリングには XAML 関連の制限はありません。

CPU と GPU の両方のメモリ使用量がカウントされることに注意してください。 Direct3D 11 は仮想グラフィックスメモリをスワップできますが、一部またはすべての XAML GPU リソースをスワップできない可能性があり、パフォーマンスが著しく低下する可能性があります。 どちらの方法でも、不要な XAML 機能を読み込まないと、アプリのためのスペースが増え、エクスペリエンスが向上します。

## <a name="xaml-view-switching-workflow"></a>XAML ビューの切り替えワークフロー

XAML からイマーシブモードに直接移動するアプリのワークフローは、次のようになります。
* アプリが 2D XAML ビューで開始されます。
* アプリの XAML スタートアップシーケンスは、現在のシステムが holographic のレンダリングをサポートしているかどうかを検出します。
* その場合は、アプリによってイマーシブビューが作成され、すぐに前面に移動します。 Xaml の読み込みは、XAML ビューでのレンダリングクラスや資産の読み込みなど、Windows Mixed Reality デバイスでは不要なものに対してスキップされます。 アプリでキーボード入力に XAML が使用されている場合でも、その入力ページは作成されます。
* それ以外の場合、XAML ビューは通常どおりビジネスで続行できます。

## <a name="tip-for-rendering-graphics-across-both-views"></a>両方のビューでグラフィックスをレンダリングするためのヒント

Windows Mixed Reality の XAML ビューに対して、DirectX で一定量のレンダリングを実装する必要がある場合、最良の方法は、両方のビューを使用できるレンダラーを1つ作成することです。 レンダラーは、両方のビューからアクセスできる1つのインスタンスである必要があり、2D と holographic のレンダリングを切り替えることができる必要があります。 これにより、GPU 資産は一度だけ読み込まれます。これにより、読み込み時間、メモリの影響、およびビューを切り替えるときにスワップされるリソースの量が減少します。
