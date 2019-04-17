---
title: DirectX の開発の概要
description: Windows Mixed Reality Api を直接使用複合現実の DirectX ベース エンジンを構築します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX、holographic レンダリング、ネイティブなネイティブ アプリ、WinRT、WinRT アプリでは、プラットフォーム Api、カスタム エンジンは、ミドルウェア
ms.openlocfilehash: 047144cb8fcf158f74375e9ec69dca92a2a1cf01
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598631"
---
# <a name="directx-development-overview"></a>DirectX の開発の概要

Windows Mixed Reality アプリの使用、 [holographic レンダリング](rendering.md)、[視線](gaze.md)、[ジェスチャ](gestures.md)、[モーションのコント ローラー](motion-controllers.md)、[音声](voice-input.md)と[空間マッピング](spatial-mapping.md)Api を構築する[複合現実](mixed-reality.md)HoloLens とイマーシブ ヘッドセットで発生します。 の 3D エンジンを使用して複合現実アプリを作成する[Unity](unity-development-overview.md)、DirectX 11 と Windows Mixed Reality Api を使用することもできます。 DirectX 12 が現在サポートされていないことに注意してください。 場合は、プラットフォームを直接活用している、本質的に作成する独自のミドルウェアまたはフレームワーク。 Windows Api サポートの両方で記述されたアプリC++とC#します。 使用したい場合C#をアプリケーションを利用することができます、 [SharpDX](http://sharpdx.org/)オープン ソース ソフトウェア ライブラリです。

Windows Mixed Reality サポート[2 つの種類のアプリ](app-views.md):
* **複合現実アプリ**(UWP または Win32) を使用して、 [HolographicSpace API](getting-a-holographicspace.md)表示するために、[没入型のビュー](app-views.md)ヘッドセット表示の入力をユーザーにします。
* **2D アプリ**(UWP) を使用して、DirectX、XAML または他のフレームワークをレンダリングする[2D ビュー](app-views.md#2d-views)ホーム Windows Mixed Reality でスレートをします。

DirectX の開発の間の相違点[2D のビューとビューの没入型](app-views.md)holographic に関連するレンダリングと空間的な入力は、主にします。 UWP アプリの[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)または Win32 アプリケーションの HWND がまだ必要でままとほとんど同じですが、アプリに利用できる WinRT Api と同様です。 ただし、holographic の機能を活用するためにこれらの Api のさまざまなサブセットを使用します。 たとえば、スワップ チェーンは holographic アプリは、システムによって管理され、DXGI にではなく、HolographicSpace API を使用する[フレームを提示](rendering-in-directx.md)します。

体感型アプリを開発するには。
* **UWP アプリ**、 [Visual Studio でテンプレートを使用して新しい UWP プロジェクトを作成する](creating-a-holographic-directx-project.md)します。 言語に基づく**Visual C++** または**Visual C#** 、下の UWP テンプレート**Windows ユニバーサル** >  **Holographic**します。
* **Win32 アプリ**、[新しい Win32 デスクトップ プロジェクトを作成](creating-a-holographic-directx-project.md#creating-a-win32-project)しに Win32 の指示に従います、[取得、HolographicSpace](getting-a-holographicspace.md) HolographicSpace を取得するページ。

これは、既存のアプリまたはエンジンに holographic のレンダリングのサポートを追加する必要があるコードを取得する優れた方法です。 リアルタイムの対話型ソフトウェアの開発者にとってなじみのある方法で、テンプレートでは、コードと概念が表示されます。

## <a name="getting-started"></a>概要

次のトピックでは、DirectX ベースのミドルウェアに Windows Mixed Reality サポートを追加する基本的な要件について説明します。
* [Holographic DirectX プロジェクトを作成する](creating-a-holographic-directx-project.md):ドキュメントと組み合わせて holographic アプリ テンプレートを使用していると、頭の上に、動作するように設計がデバイスによって導入された特別な要件の違いを示します。
* [取得、HolographicSpace](getting-a-holographicspace.md):最初に、作成、HolographicSpace では、アプリをレンダリングする元となる各ヘッドの位置を表す HolographicFrame オブジェクトのシーケンスを指定する必要があります。
* [DirectX でレンダリング](rendering-in-directx.md):Holographic スワップ チェーンには、2 つのレンダー ターゲットがあるので可能性があります、アプリケーションの表示方法にいくつかの変更を加える必要があります。
* [DirectX の座標系](coordinate-systems-in-directx.md):Windows Mixed Reality は、学習し、アプリ空間アンカーとユーザーの定義の空間ステージを含むユーザーの環境について推論を使用して空間座標系を提供する、ユーザーの手順として、世界中の内容を理解を更新します。

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>複合現実の機能および入力の追加

体感型アプリのユーザーの最良のエクスペリエンスを有効にするために、次のキー構成要素をサポートするために。
* [視線、ジェスチャ、および DirectX でモーション コント ローラー](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [DirectX での音声入力](voice-input-in-directx.md)
* [DirectX での空間のサウンド](spatial-sound-in-directx.md)
* [DirectX での空間のマッピング](spatial-mapping-in-directx.md)

これには他の主要な機能は、多くの魅力的なアプリを使用する DirectX アプリにも公開されているがあります。
* [DirectX のアンカー空間の共有](shared-spatial-anchors-in-directx.md)
* [DirectX の場所を特定できるカメラ](locatable-camera-in-directx.md)
* [キーボード、マウス、および DirectX でコント ローラーの入力](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>関連項目
* [アプリ モデル](app-model.md)
* [アプリのビュー](app-views.md)
