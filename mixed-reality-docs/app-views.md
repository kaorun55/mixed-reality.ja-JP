---
title: アプリ ビュー
description: Windows Mixed Reality アプリでのビューの 2 つの種類とは、没入型のビューと 2D のビューです。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 2D ビュー、スレート、アプリ、没入型の表示
ms.openlocfilehash: 2cf65941616ac6906d40e4b4616311317ac705d3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604731"
---
# <a name="app-views"></a>アプリ ビュー

Windows アプリは、ビューの 2 つの種類を含めることができます**没入型ビュー**と**2D ビュー**します。 アプリは、各種の没入型のビューや 2D ビュー、またはスレート型としてヘッドセットをウィンドウとしてのモニターでいずれかの 2D のビューの表示の間で切り替えることができます。 没入型の少なくとも 1 つのビューを必要とするアプリケーションは、として分類**複合現実アプリ**します。 決して没入型のビューが存在するアプリは**2D アプリ**します。

## <a name="immersive-views"></a>没入型のビュー

没入型のビューは、世界でホログラムを作成したり、仮想環境でユーザーが利用できる機能をアプリに提供します。 同時に他のアプリが描画しない描画する場合、アプリは、没入型のビューで、&mdash;複数のアプリからホログラムな複合しない組み合わせです。 継続的にパースペクティブを調整することによって、[アプリのレンダリング](rendering.md)ユーザーの頭の動きを一致するように、シーン、アプリで表示できる[world ロック](coordinate-systems.md)実際の固定の時点で残っているホログラム世界では、またはそれには、ユーザーがそこに移動すると、その位置を保持する仮想世界をレンダリングできます。

![没入型の表示の場合は、世界でホログラムを配置できます。](images/designoverview.jpg)<br>
*世界で、没入型の表示でホログラムを配置することができます。*

[HoloLens](hololens-hardware-details.md)アプリは、ユーザーの実際の環境の上にそのホログラムを表示します。 [Windows Mixed Reality イマーシブ ヘッドセット](immersive-headset-hardware-details.md)、現実の世界を表示することはできませんし、アプリをすべて表示する必要がありますように、ユーザーが表示されます。

[Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)中に、没入型 ([スタート] メニューと、環境を配置したホログラムを含む) が表示されないかを表示します。 HoloLens で没入型のビューが表示されている間に発生したシステムの通知は、Cortana による音声で返すことリレー型し、ユーザーが音声入力に応答できます。

没入型の表示中に、アプリは、すべての入力を処理する責任を負いますがもします。 Windows Mixed Reality での入力から成る[視線](gaze.md)、[ジェスチャ](gestures.md)(HoloLens のみ)、[音声](voice-input.md)と[コント ローラーのモーション](motion-controllers.md)(没入型ヘッドセットのみ)。

## <a name="2d-views"></a>2D のビュー

![複数の 2D ビューが home、Windows Mixed Reality をレイアウト](images/teleportation-640px.png)<br>
*複数のアプリには、2 D のビューが home、Windows Mixed Reality の周囲に配置*

2D のビューを使用してアプリが表示されます、 [Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)("shell"とも呼ばれます) として仮想スレートでは、アプリケーション ランチャーと、ユーザーが自分の環境に配置するその他のホログラムと共に表示します。 ユーザーは、そのサイズに関係なく固定解像度のまま、このスレートを移動し、スケールを調整できます。 アプリの最初のビューが 2D のビューの場合は、2 D コンテンツは、アプリを起動するために使用する同じスレートを入力します。

デスクトップ ヘッドセット、今日、デスクトップ モニター上で実行されるすべてのユニバーサル Windows プラットフォーム (UWP) アプリを実行できます。 これらのアプリは現在、2 D ビューをレンダリングされて既にとそのコンテンツは自動的に起動すると、ユーザーの世界中のスレートの表示されます。 2D の UWP アプリを対象にできます、 **Windows.Universal**デスクトップ両方ヘッドセットと HoloLens スレートとして実行するデバイスのファミリです。

システム キーボードの 2D のビューのキーの使用ができるようにするテキスト エントリ フォームを表示するには 1 つ使用します。 シェルは、没入型のビューの上部にレンダリングできません、ため、アプリが 2D システム キーボードを表示するビューを切り替える必要があります。 テキスト入力をそのまま使用するアプリは、テキスト ボックスと、2 D 表示に切り替えることができます。 そのテキスト ボックスにフォーカスがあるは、ユーザーがテキストを入力できるように、システムのキーボードが表示されます。

デスクトップ PC にアプリを持つことができる、アタッチされたヘッドセットとデスクトップの両方のモニターで 2D のビューに注意してください。 たとえば、その主な 2D のビューを使用して、360 度のビデオを検索するデスクトップ モニター エッジを参照できます。 そのビデオを再生する場合、エッジは没入型のビデオ コンテンツを表示するヘッドセット内セカンダリ没入型のビューを起動します。

## <a name="see-also"></a>関連項目

* [アプリ モデル](app-model.md)
* [複合現実の 2D の UWP アプリを更新します。](building-2d-apps.md)
* [HolographicSpace を取得します。](getting-a-holographicspace.md)
* [Windows Mixed Reality ホームに移動します。](navigating-the-windows-mixed-reality-home.md)
* [複合現実アプリの種類](types-of-mixed-reality-apps.md)
