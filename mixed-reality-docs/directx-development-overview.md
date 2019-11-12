---
title: DirectX 開発の概要
description: Windows Mixed Reality Api を直接使用して、DirectX ベースの混合現実エンジンをビルドします。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, holographic レンダリング, ネイティブ, ネイティブアプリ, WinRT, WinRT アプリ, プラットフォーム Api, カスタムエンジン, ミドルウェア
ms.openlocfilehash: 0af73314c3c93d230ef87ed468f718f5b3e1813c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926625"
---
# <a name="directx-development-overview"></a>DirectX 開発の概要


Windows [Mixed reality アプリケーション](mixed-reality.md)は、 [holographic レンダリング](rendering.md)、[宝石](gaze-and-commit.md)、[ジェスチャ](gaze-and-commit.md#composite-gestures)、[モーションコントローラー](motion-controllers.md)、[音声](voice-input.md)、および[空間マッピング](spatial-mapping.md)api を使用して、HoloLens とイマーシブヘッドセット。 [Unity](unity-development-overview.md)などの3d エンジンを使用して mixed reality アプリケーションを作成することも、directx 11 または directx 12 を使用して Windows Mixed reality api に直接コードを記述することもできます。 プラットフォームを直接利用する場合は、基本的に独自のミドルウェアまたはフレームワークを構築することになります。 Windows Api は、とC++ C#の両方で記述されたアプリケーションをサポートします。 を使用C#することを選択した場合、アプリケーションは[SharpDX](https://sharpdx.org/)オープンソースソフトウェアライブラリを利用できます。


Windows Mixed Reality は[、次の2種類のアプリを](app-views.md)サポートしています。
* [HOLOGRAPHICSPACE API](getting-a-holographicspace.md)を使用して、ヘッドセットの表示を満たすユーザーに[イマーシブビュー](app-views.md)をレンダリングする**Mixed reality アプリケーション**(UWP または Win32)。
* DirectX、XAML、またはその他のフレームワークを使用して、Windows Mixed Reality ホームのスレートに[2d ビュー](app-views.md#2d-views)をレンダリングする**2d アプリ**(UWP)。


[2d ビューとイマーシブビュー](app-views.md)の DirectX 開発の違いは、主に holographic のレンダリングと空間入力に関連しています。 UWP アプリケーションの[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)または Win32 アプリケーションの HWND が必要であり、アプリケーションで使用できる WinRT api と同様に、ほとんど同じままです。 ただし、holographic 機能を利用するには、これらの Api の異なるサブセットを使用する必要があります。 たとえば、スワップチェーンは、holographic アプリケーション用にシステムによって管理されます。 [フレームを表示](rendering-in-directx.md)するには、DXGI ではなく HolographicSpace API を使用します。

イマーシブアプリケーションの開発を開始するには:
* **Uwp アプリ**の場合は、 [Visual Studio のテンプレートを使用して新しい UWP プロジェクトを作成](creating-a-holographic-directx-project.md)します。 お使いの言語、**ビジュアルC++**  、または**ビジュアルC#** に基づいて、 **Windows Universal** > **Holographic**の UWP テンプレートを見つけることができます。
* **Win32 アプリケーション**の場合は、 [ *basichologram* Win32 サンプルから開始](creating-a-holographic-directx-project.md#creating-a-win32-project)します。

これは、既存のアプリケーションまたはエンジンに holographic のレンダリングサポートを追加するために必要なコードを取得するための優れた方法です。 コードと概念は、リアルタイムの対話型ソフトウェアの開発者にとって使い慣れた方法でテンプレートに記載されています。


## <a name="getting-started"></a>開始するには

次のトピックでは、Windows Mixed Reality サポートを DirectX ベースのミドルウェアに追加するための基本要件について説明します。

* [Holographic DirectX プロジェクトを作成](creating-a-holographic-directx-project.md)する: holographic アプリケーションテンプレートとドキュメントを組み合わせると、使用しているものと、機能するように設計されたデバイスによって導入された特別な要件の違いが示されます。をお待ちしています。
* [HolographicSpace の取得](getting-a-holographicspace.md): 最初に、レンダリングする各ヘッドの位置を表す HolographicFrame オブジェクトのシーケンスをアプリケーションに提供する HolographicSpace を作成する必要があります。
* [DirectX でのレンダリング](rendering-in-directx.md): holographic スワップチェーンには2つのレンダーターゲットがあるため、アプリケーションのレンダリング方法にいくつかの変更を加える必要があります。
* [DirectX でのシステムの調整](coordinate-systems-in-directx.md): Windows Mixed Reality は、ユーザーが説明しているとおりに世界の理解を深め、更新します。 これにより、空間アンカーやユーザーが定義した空間ステージなど、ユーザーの環境についての理由にアプリケーションが使用する空間座標系が提供されます。

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Mixed reality 機能と入力の追加

イマーシブアプリケーションのユーザーに最適なエクスペリエンスを実現するには、次の主要な構成要素をサポートする必要があります。

* [DirectX でのヘッド視線入力とアイ視線入力](gaze-in-directx.md)
* [DirectX での手とモーション コントローラー](hands-and-motion-controllers-in-directx.md)
* [DirectX の音声入力](voice-input-in-directx.md)
* [立体音響](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [DirectX の空間マッピング](spatial-mapping-in-directx.md)


多くのイマーシブアプリケーションでは、DirectX アプリケーションにも公開されている主な機能が使用されます。

* [DirectX での共有された空間アンカー](shared-spatial-anchors-in-directx.md)
* [DirectX でのキーボード、マウス、およびコントローラー入力](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>関連項目
* [アプリ モデル](app-model.md)
* [アプリ ビュー](app-views.md)
