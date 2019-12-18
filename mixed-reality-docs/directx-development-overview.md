---
title: ネイティブ開発の概要
description: Windows Mixed Reality Api を直接使用して、DirectX ベースの mixed reality エンジンをビルドします。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, holographic レンダリング, ネイティブ, ネイティブアプリ, WinRT, WinRT アプリ, プラットフォーム Api, カスタムエンジン, ミドルウェア
ms.openlocfilehash: 06227b41dde69e6610b151f3b27a3800e76431bd
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181902"
---
# <a name="native-development-overview"></a>ネイティブ開発の概要

Windows Mixed Reality アプリケーションは、次の Api を使用して、HoloLens とその他のイマーシブヘッドセットの[Mixed Reality](mixed-reality.md)エクスペリエンスを構築します。

 - [ホログラフィック レンダリング](rendering.md)
 - [視線入力](gaze-and-commit.md)
 - [ジェスチャ](gaze-and-commit.md#composite-gestures)
 - [モーションコントローラー](motion-controllers.md)
 - [音声](voice-input.md)
 - [空間マッピング](spatial-mapping.md)

[Unity](unity-development-overview.md)などの3d エンジンを使用して、mixed reality アプリケーションを作成できます。 または、DirectX 11 または DirectX 12 を使用して、Windows Mixed Reality Api に直接コードを記述することもできます。 プラットフォームを直接利用する場合は、基本的に独自のミドルウェアまたはフレームワークを構築します。 Windows Api は、とC++ C#の両方で記述されたアプリケーションをサポートしています。 を使用C#する場合、アプリケーションは[SharpDX](https://sharpdx.org/)オープンソースソフトウェアライブラリを利用できます。

Windows Mixed Reality は[、次の2種類のアプリを](app-views.md)サポートしています。
* [HOLOGRAPHICSPACE API](getting-a-holographicspace.md)を使用して、ヘッドセットの表示を満たすユーザーに[イマーシブビュー](app-views.md)をレンダリングする**Mixed reality アプリケーション**(UWP または Win32)
* DirectX、XAML、または別のフレームワークを使用して、Windows Mixed Reality ホームのスレートに[2d ビュー](app-views.md#2d-views)をレンダリングする**2d アプリ**(UWP)

[2d ビューとイマーシブビュー](app-views.md)の DirectX 開発の違いは、主に holographic のレンダリングと空間入力に関係しています。 UWP アプリケーションの[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)または Win32 アプリケーションの HWND が必要であり、ほぼ同じです。 アプリで使用できる WinRT Api にも同じことが当てはまります。 ただし、holographic 機能を利用するには、これらの Api の異なるサブセットを使用する必要があります。 たとえば、スワップチェーンは、holographic アプリケーション用にシステムによって管理されます。 また、[フレームを表示](rendering-in-directx.md)するには、DXGI ではなく HolographicSpace API を使用します。

イマーシブアプリケーションの開発を開始するには:
* **Uwp アプリ**の場合は、Visual Studio のテンプレートを使用して、[新しい UWP プロジェクトを作成](creating-a-holographic-directx-project.md)します。 お使いの言語、ビジュアルC++ 、またC#はビジュアルに基づいて、 **WINDOWS Universal** > **Holographic**の UWP テンプレートを見つけます。
* **Win32 アプリケーション**の場合は、 [ *basichologram* Win32 サンプルから開始](creating-a-holographic-directx-project.md#creating-a-win32-project)します。

この手順は、既存のアプリケーションまたはエンジンに holographic のレンダリングサポートを追加するために必要なコードを取得するための優れた方法です。 コードと概念は、リアルタイムの対話型ソフトウェアの開発者にとって使い慣れた方法でテンプレートに記載されています。

## <a name="get-started"></a>、

次のトピックでは、Windows Mixed Reality サポートを DirectX ベースのミドルウェアに追加する際の基本要件について説明します。

* [Holographic DirectX プロジェクトを作成](creating-a-holographic-directx-project.md)する: holographic アプリケーションテンプレートとドキュメントを組み合わせると、使用しているものと比較した場合の相違点が示されます。 また、ヘッドに置いて機能するように設計されているデバイスの特別な要件についても説明します。
* [HolographicSpace の取得](getting-a-holographicspace.md): 最初に、レンダリングする各ヘッドの位置を表す HolographicFrame オブジェクトのシーケンスをアプリケーションに提供する HolographicSpace を作成する必要があります。
* [DirectX でのレンダリング](rendering-in-directx.md): holographic スワップチェーンには2つのレンダーターゲットがあるため、アプリのレンダリング方法にいくつかの変更を加える必要があります。
* [DirectX でのシステムの調整](coordinate-systems-in-directx.md): Windows Mixed Reality は、ユーザーが説明しているとおりに世界の理解を深め、更新します。 これにより、空間アンカーやユーザーが定義した空間ステージなど、ユーザーの環境についての理由にアプリケーションが使用する空間座標系が提供されます。

## <a name="add-mixed-reality-capabilities-and-inputs"></a>Mixed reality の機能と入力を追加する

イマーシブアプリのユーザーに最適なエクスペリエンスを提供するには、次の主要な構成要素をサポートする必要があります。

* [DirectX でのヘッド視線入力とアイ視線入力](gaze-in-directx.md)
* [DirectX での手とモーション コントローラー](hands-and-motion-controllers-in-directx.md)
* [DirectX の音声入力](voice-input-in-directx.md)
* [立体音響](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [DirectX の空間マッピング](spatial-mapping-in-directx.md)

これらは、多くのイマーシブアプリケーションが DirectX アプリケーションにも公開する主な機能です。

* [DirectX での共有された空間アンカー](shared-spatial-anchors-in-directx.md)
* [DirectX でのキーボード、マウス、およびコントローラー入力](keyboard-mouse-and-controller-input-in-directx.md)

## <a name="see-also"></a>関連項目
* [アプリ モデル](app-model.md)
* [アプリ ビュー](app-views.md)
