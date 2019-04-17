---
title: Holographic の DirectX アプリでの XAML の使用
description: 2D の XAML ビューと XAML ビューとビューの没入型の両方の効率的に使用する方法と、DirectX アプリで没入型のビューの切り替えの影響について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: windows mixed reality、UWP、アプリを表示、管理、xaml、キーボード チュートリアルでは、DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598684"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Holographic の DirectX アプリでの XAML の使用

このトピックでは、間の切り替えの影響を説明します。 [2D の XAML ビューとビューの没入型](app-views.md)、DirectX アプリでの XAML ビューと没入型のビューの両方を効率的に使用する方法。

## <a name="xaml-view-switching-overview"></a>XAML ビューの概要の切り替え

、HoloLens の通常没入型のアプリが 2D の XAML ビューを後で表示される場合はその XAML ビューを最初に初期化し、そこから、没入型のビューをすぐに切り替える必要があります。 つまり、XAML は、アプリが操作を実行する前に読み込まれます。 その結果、起動時間を少し増やすがあり、XAML は引き続きバック グラウンド; であるときに、アプリのプロセスのメモリ領域を占有ネイティブ ビューに切り替える前に XAML は量起動時の遅延とメモリ使用量はどのようなアプリによって異なります。 Nothing は、XAML スタートアップ、没入型の表示の開始点を除いて、最初のコードでは、影響はマイナーになります。 また、没入型のビューに直接、holographic、レンダリングが行われるために、そのレンダリングに XAML に関連する制限を適用が済みます。

CPU と GPU の両方のメモリ使用量をカウントすることに注意してください。 Direct3d11 が仮想のグラフィック メモリとスワップできるが、XAML の GPU のリソースの一部またはすべてを入れ替えることができない可能性があり、顕著なパフォーマンスに影響がある可能性があります。 どちらの方法でも、XAML の機能が読み込まれていませんしない必要があります、アプリの複数の部屋のままにして優れたエクスペリエンスを実現します。

## <a name="xaml-view-switching-workflow"></a>XAML ビューのワークフローの切り替え

ワークフローがあるイマーシブ モードに XAML から直接移動するアプリのようになります。
* 2D の XAML ビューで、アプリの起動時します。
* アプリの XAML の起動シーケンスでは、現在のシステムが holographic のレンダリングをサポートしているかを検出します。
* そうである場合、アプリは没入型のビューを作成し、すぐ、前面に表示します。 レンダリング クラスおよび XAML ビューで読み込まれる資産を含む、Windows Mixed Reality デバイス上の何もないために必要な XAML 読み込みがスキップされます。 アプリはキーボード入力の XAML を使用している場合は、その入力ページを作成もする必要があります。
* それ以外の場合は、XAML ビューが通常どおりの業務を続行できます。

## <a name="tip-for-rendering-graphics-across-both-views"></a>両方のビューで、グラフィックのレンダリングをヒントします。

を、アプリが Windows Mixed Reality で XAML ビューの DirectX で一定のレンダリングを実装する必要がある場合、最善の方法では、両方のビューで動作する 1 つのレンダラーを作成します。 レンダラーが両方のビューからアクセスできる 1 つのインスタンスにする必要があり、2 D および holographic の表示を切り替えることができるようにします。 読み込み時間、メモリへの影響、およびビューを切り替えるときにスワップするリソースの量を減少この GPU 資産は 1 回のみ読み込むようにします。
