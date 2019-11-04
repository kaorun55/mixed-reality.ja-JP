---
title: アプリ ビュー
description: Windows Mixed Reality アプリの2種類のビューは、イマーシブビューと2D ビューです。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: イマーシブビュー、2D ビュー、スレート、アプリ
ms.openlocfilehash: a5b50df5be31d66a866e691d9e059bcf38672064
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437017"
---
# <a name="app-views"></a>アプリ ビュー

Windows アプリには、2種類のビュー、**イマーシブビュー** 、および**2d ビュー**を含めることができます。 アプリでは、さまざまなイマーシブビューと2D ビューを切り替えることができます。モニター上の2D ビューは、ウィンドウとして、またはヘッドセットにスレートとして表示されます。 少なくとも1つのイマーシブビューを持つアプリは、 **mixed reality アプリ**として分類されます。 イマーシブビューを持たないアプリは、 **2d アプリ**です。

## <a name="immersive-views"></a>イマーシブビュー

イマーシブビューを使用すると、お客様のアプリは、ユーザーの周囲にホログラムを作成したり、仮想環境でユーザーをこちらしたりすることができます。 アプリがイマーシブビューで描画されている場合、同時に他のアプリが描画されることはありません&mdash;複数のアプリからのホログラムは一緒に合成されません。 アプリがユーザーのヘッド移動に合わせてシーンを[レンダリング](rendering.md)するパースペクティブを継続的に調整することにより、アプリでは、現実世界の固定されたポイントにとどまっている[世界中にロック](coordinate-systems.md)されたホログラムをレンダリングしたり、ユーザーがその内部で移動する位置。

![イマーシブビューでは、ホログラムを世界中に配置できます。](images/designoverview-940px.jpg)<br>
*イマーシブビューでは、ホログラムを世界中に配置できます。*

[HoloLens](hololens-hardware-details.md)では、アプリはユーザーの実際の環境の上にホログラムをレンダリングします。 [Windows Mixed Reality のイマーシブヘッドセット](immersive-headset-hardware-details.md)では、ユーザーは実際の世界を見ることができないため、ユーザーに表示されるすべてのものをアプリでレンダリングする必要があります。

[Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)(環境の周囲に配置した [スタート] メニューとホログラムを含む) は、イマーシブビューでは表示されません。 HoloLens では、イマーシブビューが表示されている間に発生するシステム通知は、Cortana によって音声でリレーされ、ユーザーは音声入力を使用して応答できます。

イマーシブビューでは、すべての入力を処理することもアプリに任されています。 Windows Mixed Reality での入力は、[宝石](gaze-and-commit.md)、[ジェスチャ](gaze-and-commit.md#composite-gestures)(HoloLens のみ)、[音声](voice-input.md)および[モーションコントローラー](motion-controllers.md) (イマーシブヘッドセットのみ) で構成されています。

## <a name="2d-views"></a>2D ビュー

Windows Mixed Reality ホーム](images/teleportation-940px.png) 周囲にレイアウトされた複数の2D ビュー ![<br>
*Windows Mixed Reality ホームの周囲に2D ビューが配置された複数のアプリ*

2D ビューを使用するアプリは、 [Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)("シェル" とも呼ばれます) に仮想スレートとして表示されます。これは、アプリランチャーと、ユーザーが世界中に配置したその他のホログラムと共にレンダリングされます。 ユーザーは、サイズに関係なく固定された解像度でも、このスレートを調整してスケールすることができます。 アプリの最初のビューが2D ビューの場合、2D コンテンツはアプリを起動するために使用されるものと同じスレートに収まるようになります。

デスクトップヘッドセットでは、現在デスクトップモニター上で実行されている任意のユニバーサル Windows プラットフォーム (UWP) アプリを実行できます。 これらのアプリは既に2D ビューをレンダリングしており、そのコンテンツは、起動時にユーザーの世界のスレートに自動的に表示されます。 2D UWP アプリは、デスクトップヘッドセットと HoloLens on スレートの両方で動作するように**Windows ユニバーサル**デバイスファミリをターゲットにすることができます。

2D ビューの主な用途の1つは、システムキーボードを利用できるテキスト入力フォームを表示することです。 シェルは、イマーシブビューの上にレンダリングできないため、アプリケーションは、システムキーボードを表示するために2D ビューに切り替える必要があります。 テキスト入力を受け入れるアプリでは、テキストボックスを使用して2D ビューに切り替えることができます。 このテキストボックスにフォーカスがあるときは、システムキーボードが表示され、ユーザーはテキストを入力できます。

デスクトップ PC では、アプリはデスクトップモニターと接続されたヘッドセットの両方に2D ビューを持つことができます。 たとえば、メインの2D ビューを使用してデスクトップモニターのエッジを参照し、360度のビデオを見つけることができます。 このビデオを再生すると、Edge は、ヘッドセット内の2次的なイマーシブビューを起動して、イマーシブビデオコンテンツを表示します。

## <a name="see-also"></a>関連項目

* [アプリ モデル](app-model.md)
* [複合現実の 2D UWP アプリを更新する](building-2d-apps.md)
* [HolographicSpace を入手する](getting-a-holographicspace.md)
* [Windows Mixed Reality ホームのナビゲーション](navigating-the-windows-mixed-reality-home.md)
* [複合現実アプリの種類](types-of-mixed-reality-apps.md)
