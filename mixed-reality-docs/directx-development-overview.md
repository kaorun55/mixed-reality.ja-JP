---
title: DirectX の開発の概要
description: Windows Mixed Reality Api を直接使用複合現実の DirectX ベース エンジンを構築します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX、holographic レンダリング、ネイティブなネイティブ アプリ、WinRT、WinRT アプリでは、プラットフォーム Api、カスタム エンジンは、ミドルウェア
ms.openlocfilehash: da6beae6e256fef49481b581395e507b3f2acd04
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414381"
---
# <a name="directx-development-overview"></a>DirectX の開発の概要


Windows Mixed Reality アプリケーションを使用して、 [holographic レンダリング](rendering.md)、[視線](gaze.md)、[ジェスチャ](gestures.md)、[モーションのコント ローラー](motion-controllers.md)、 [音声](voice-input.md)と[空間マッピング](spatial-mapping.md)Api を構築する[複合現実](mixed-reality.md)HoloLens とイマーシブ ヘッドセットで発生します。 の 3D エンジンを使用して複合現実のアプリケーションを作成する[Unity](unity-development-overview.md)、または DirectX 11 または DirectX 12 を使用して Windows 混合現実 Api に対して直接コーディングすることができます。 場合は、プラットフォームを直接活用している、本質的に作成する独自のミドルウェアまたはフレームワーク。 Windows Api サポートの両方で記述されたアプリケーションC++とC#します。 使用する場合C#をアプリケーションを利用することができます、 [SharpDX](http://sharpdx.org/)オープン ソース ソフトウェア ライブラリです。


Windows Mixed Reality サポート[2 つの種類のアプリ](app-views.md):
* **実際のアプリケーションを混合**(UWP または Win32) を使用する、 [HolographicSpace API](getting-a-holographicspace.md)表示するために、[没入型のビュー](app-views.md)ヘッドセット表示の入力をユーザーにします。
* **2D アプリ**(UWP) を使用して、DirectX、XAML、またはその他のフレームワークをレンダリングする[2D ビュー](app-views.md#2d-views)ホーム Windows Mixed Reality でスレートをします。


DirectX の開発の間の相違点[2D のビューとビューの没入型](app-views.md)holographic に関連するレンダリングと空間的な入力は、主にします。 UWP アプリケーションの[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)または Win32 アプリケーションの HWND が必要なままとほとんど同じですが、アプリケーションで利用できる WinRT Api と同様です。 ただし、holographic の機能を活用するために、これらの Api のさまざまなサブセットを使用する必要があります。 たとえば、スワップ チェーンは、holographic appslications のシステムによって管理されます。 DXGI にではなく、HolographicSpace API を使用する[フレームを提示](rendering-in-directx.md)します。

没入型アプリケーションを開発するには。
* **UWP アプリ**、 [Visual Studio でテンプレートを使用して新しい UWP プロジェクトを作成する](creating-a-holographic-directx-project.md)します。 言語に基づく**Visual C++** または**Visual C#** で UWP テンプレートを見つける**Windows ユニバーサル** >  **Holographic**します。
* **Win32 アプリケーション**、[からを起動、 *BasicHologram* Win32 サンプル](creating-a-holographic-directx-project.md#creating-a-win32-project)します。

これは、既存のアプリケーションまたはエンジンに holographic のレンダリングのサポートを追加する必要のあるコードを取得する優れた方法です。 リアルタイムの対話型ソフトウェアの開発者にとってなじみのある方法で、テンプレートでは、コードと概念が表示されます。


## <a name="getting-started"></a>概要

次のトピックでは、DirectX ベースのミドルウェアに Windows Mixed Reality サポートを追加する基本的な要件について説明します。

* [Holographic DirectX プロジェクトを作成する](creating-a-holographic-directx-project.md):ドキュメントと組み合わせて、holographic アプリケーション テンプレートを使用しているだけでなく、頭の上に、動作するように設計がデバイスによって導入された特別な要件の違いを示します。
* [取得、HolographicSpace](getting-a-holographicspace.md):最初に、アプリケーションにレンダリングするが各ヘッドの位置を表す HolographicFrame オブジェクトのシーケンスを提供する HolographicSpace を作成する必要があります。
* [DirectX でレンダリング](rendering-in-directx.md):Holographic スワップ チェーンには、2 つのレンダー ターゲットがあるので、アプリケーションの表示方法にいくつかの変更を加える必要があります。
* [DirectX の座標系](coordinate-systems-in-directx.md):Windows Mixed Reality は、学習し、更新プログラムのように、ユーザーの周囲を歩き、世界中の理解します。 これは、アプリケーション空間のアンカーを含むユーザーの環境について推論を使用して、ユーザーの空間ステージを定義する空間座標系を提供します。

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>複合現実の機能および入力の追加

没入型 appslication のユーザーの最良のエクスペリエンスを有効にするために、次のキー構成要素をサポートするために。

* [DirectX でのヘッド視線入力とアイ視線入力](gaze-in-directx.md)
* [DirectX での手とモーション コントローラー](hands-and-motion-controllers-in-directx.md)
* [DirectX の音声入力](voice-input-in-directx.md)
* [DirectX の立体音響](spatial-sound-in-directx.md)
* [DirectX の空間マッピング](spatial-mapping-in-directx.md)


その他の主要機能は、多くの没入型アプリケーションを使用する DirectX アプリケーションにも公開されているがあります。

* [DirectX での共有された空間アンカー](shared-spatial-anchors-in-directx.md)
* [DirectX での場所を特定できるカメラ](locatable-camera-in-directx.md)
* [DirectX でのキーボード、マウス、およびコントローラー入力](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>関連項目
* [アプリ モデル](app-model.md)
* [アプリ ビュー](app-views.md)
