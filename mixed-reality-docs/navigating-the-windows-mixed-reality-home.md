---
title: Windows Mixed Reality ホームに移動します。
description: HoloLens と Windows Mixed Reality ヘッドセットは、起動、配置すると、および (物理またはデジタル) かどうかは、アプリと、環境内の 3D モデルを操作するためのパラダイムを共有します。 両方のデバイスの種類でホーム Windows Mixed Reality を移動する方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: シェル、os、プラットフォーム、cliff 家、家、ホーム、環境、開始、[スタート] メニューのホーム メニューの pin、アプリ、アプリの起動、テレポート、アプリを配置、移動、移動します
ms.openlocfilehash: 1ca6dd66506a64ad2e1c21870fee2725ddf20bd8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604898"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Windows Mixed Reality ホームに移動します。

Windows PC エクスペリエンスがデスクトップで始まるよう Windows Mixed Reality ホームから始まります。 Windows Mixed Reality ホームは、本質的な機能を理解し、3 D の場所を移動を活用します。 HoloLens、自宅は、実際の場所です。 イマーシブ ヘッドセット、自宅は仮想の場所です。

自宅は、[スタート] メニューを開き、アプリやコンテンツを配置に使用する場所もです。 複合現実のコンテンツを自宅に入力し、同時に複数のアプリを使用して、マルチタスクを実行できます。 自宅に配置することは、デバイスを再起動する場合でも、ままです。

## <a name="start-menu"></a>スタート メニュー

![Microsoft HoloLens の [スタート] メニュー](images/start-500px.png)

[スタート] メニューから成ります。
* システム情報 (ネットワークの状態、バッテリの残量割合、現在の時刻およびボリューム)
* Cortana (イマーシブ ヘッドセット、スタート タイルで、開始の上部にある、HoloLens 用)
* ピン留めされたアプリ
* すべてのアプリ (プラス記号)
* 写真とビデオのボタンを[実際のキャプチャの混在](mixed-reality-capture.md)

ビューを切り替えるピン留めされたアプリおよびすべてのアプリ間でプラス記号を選択するか、またはマイナス ボタン。 HoloLens で [スタート] メニューを開くには、するには、「bloom ジェスチャを使用します。 イマーシブ ヘッドセットでは、上には、コント ローラーの Windows ボタンを押します。

## <a name="launching-apps"></a>アプリの起動

アプリを起動するには、開始時に選択します。 [スタート] メニューは表示されなくなり、2D のウィンドウとしての配置モードで、アプリが開きますまたは[3D モデル](implementing-3d-app-launchers.md)します。

アプリを実行するには、自宅に配置する必要があります。
1. 使用して、[視線](gaze.md)またはコント ローラーにすることをアプリに位置します。 自動的に、(サイズと位置) に配置する領域に準拠するために調整されます。
2. エア タップ (HoloLens) または [選択] ボタン (イマーシブ ヘッドセット) を使用してアプリを配置します。 キャンセルして、[スタート] メニューを元に戻します、ブルーム ジェスチャまたは Windows ボタンを使用します。

[2D アプリ](building-2d-apps.md)、デスクトップ、モバイル、用に作成またはを使用して複合現実体感型アプリとして実行する Xbox を変更することができます、 [HolographicSpace API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)します。 没入型のアプリは、自宅外には」および「魅力的なエクスペリエンスにユーザーを受け取ります。 ユーザーは、「bloom ジェスチャ (HoloLens) または、コント ローラー (イマーシブ ヘッドセット) の Windows ボタンを押して、ホーム返すできます。

アプリへの API を使用して、または Cortana 経由でアプリを起動することもできます。

![ホーム Windows Mixed Reality アプリ](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>移動して、アプリを調整します。

選択**調整**アプリでバーを表示するが、スケール、移動を制御し、混在した実際のコンテンツを回転します。 完了したら、選択**完了**します。

![調整モード (青色の枠) ストアへのスレートします。 アプリ バーに注意してください (上) が '完了' と 'Remove' を含むように変更がボタン。](images/adjust-500px.png)

別のアプリ、アプリ バーで、追加のオプションがあります。 たとえば、Microsoft Edge が*スクロール*、*ドラッグ*、および*ズーム*選択肢です。 

![HoloLens で実行されている 2D アプリ用アプリ バー](images/holobar-500px.png)

**戻る**ボタンが、アプリで表示されていた画面に移動します。 アプリを示した他のアプリに移動 エクスペリエンスの先頭に到達したときに停止します。

## <a name="getting-around-your-home"></a>自宅の回避

**HoloLens**自宅内を移動する物理領域間を移動します。

**イマーシブ ヘッドセット**、同様にを取得し、仮想世界のような領域内を移動する、playspace で歩き回りできます。 距離が長い間を移動するにするまたはを使用して、スティック コント ローラーを事実上"、"を使用することができます*teleportation*距離が長いをすぐにジャンプします。

![Windows Mixed Reality ホームで Teleportation](images/teleportation-500px.png)

**テレポート: に**
1. Teleportation 十字線を表示します。
   * 使用して[コント ローラーのモーション](motion-controllers.md): スティックを進むキーを押して、その位置に押したままにします。
   * Xbox コント ローラーを使用して: 左のサムスティックを進むキーを押して、その位置に押したままにします。
   * マウスを使用して: 右マウス ボタンを押しながら (ときに直面する方向を回転するスクロール ホイールを使用し、するテレポート)。
2. テレポートしたい、十字線を配置します。
   * 使用して[コント ローラーのモーション](motion-controllers.md): の十字線を移動する (いるを維持しているスティック フォワード) コント ローラーを傾けます。
   * Xbox コント ローラーを使用して: を使用して、[視線](gaze.md)の十字線を移動します。
   * マウスを使用して: の十字線を移動する、マウスを移動します。
3. テレポート、目盛りが配置された場所にボタンを離します。

**事実上"について説明します"。**
* 使用して[コント ローラーのモーション](motion-controllers.md): スティックを押したままをクリックし、スティックを「について説明します。」したい方向に移動します。
* Xbox コント ローラーを使用します。 左のサムスティックを押したまま、をクリックし、スティックを"について説明します。"したい方向に移動します。

## <a name="immersive-headset-input-support"></a>イマーシブ ヘッドセット入力のサポート

[Windows Mixed Reality イマーシブ ヘッドセット](immersive-headset-hardware-details.md)ホーム Windows Mixed Reality を移動するための複数の入力の種類をサポートします。 HoloLens は、物理的に歩き回りし、環境参照を実行するため、アクセサリの入力をナビゲーションをサポートしません。 ただし、HoloLens が[の入力をサポート](hardware-accessories.md)アプリと対話するためです。

### <a name="motion-controllers"></a>アニメーション コント ローラー

Windows Mixed Reality で最適な Windows Mixed Reality エクスペリエンスになります[コント ローラーのモーション](motion-controllers.md)ヘッドセットのない外部のカメラまたは必要なマーカーのセンサーだけを使用してそのサポート 6 自由度の追跡。

近日公開予定のナビゲーション コマンド。

### <a name="gamepad"></a>ゲームパッド
* **左のサムスティック:**
  * 左のサムスティック フォワードを長押しし、 [teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)目盛り。
  * Left、right、スティックをタップまたはバックエンドを左に移動して、右、または少しずつバックアップします。
  * 左のサムスティックを押したままをクリックし、スティックを移動する方向で[事実上「について説明します」。](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* タップして、**右スティック**左または右に 45 度直面している方向を回転します。
* キーを押して、 **A**ボタンは、select を実行してのように動作、[エア タップ](gestures.md#air-tap)ジェスチャ。
* キーを押して、**ガイド**ボタンが表示されます、 [[スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)のように動作し、[ブルーム](gestures.md#bloom)ジェスチャ。
* キーを押して、**左および右のトリガー**自宅で対話する 2D のデスクトップ アプリとの間に拡大することができます。

### <a name="keyboard-and-mouse"></a>キーボードとマウス

**注:** 使用**Windows キーを押しながら Y**マウス、PC のデスクトップおよび Windows Mixed Reality ホームの制御との間を切り替える。

ホーム Windows Mixed Reality: 内
* キーを押して、**左クリック**マウスのボタンは、select を実行してのように動作、[エア タップ](gestures.md#air-tap)ジェスチャ。
* 保持している、**を右クリックして**マウス ボタンが表示されます、 [teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)目盛り。
* キーを押して、 **Windows**キーボードのキーが表示されます、 [[スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)のように動作し、[ブルーム](gestures.md#bloom)ジェスチャ。
* ときに[gazing](gaze.md) 2D のデスクトップ アプリにすることができます**左クリック**を選択する**を右クリックして**コンテキスト メニューを表示して使用する、**スクロール ホイール**スクロール (PC のデスクトップで同様)。

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana) PC、電話上と同じように Windows Mixed Reality で、パーソナル アシスタントは、します。 HoloLens は、組み込みのマイクがイマーシブ ヘッドセットは追加のハードウェアを必要があります。 Cortana をアプリを開き、デバイスを再起動、ものをオンラインで検索などを使用します。 開発者は、することもできます[Cortana の統合](https://dev.windows.com/cortana)に経験します。

自宅を回避する音声コマンドを使用することもできます。 たとえば、ボタンをポイント (を使用して[視線](gaze.md)またはコント ローラーは、デバイスによって異なります) と""を選択します。 他の音声コマンドを"Go home"、「大きい」、「より小さい、」含める「閉じる」と「直面 me」。

## <a name="store-settings-and-system-apps"></a>ストア、設定、およびシステム アプリ

Windows Mixed Reality は多くの組み込みのアプリなどがあります。
* **Microsoft Store**アプリやゲームを取得するには
* **フィードバック Hub**システムやシステム アプリに関するフィードバックを送信するには
* **設定**システム設定を構成する ([ネットワークを含む](connecting-to-wi-fi-on-hololens.md)とシステムの更新プログラム)
* **Microsoft Edge** web サイトを閲覧するには
* **写真**表示し、写真やビデオを共有するには
* **調整**(HoloLens のみ)、HoloLens、現在のユーザー エクスペリエンスを調整します。
* **ジェスチャを説明します**(HoloLens) または**Mixed Reality の学習**については、デバイスを使用して (イマーシブ ヘッドセット)。
* **3D ビューアー**複合現実のコンテンツで、世界を修飾するには
* **実際にはポータルの混合**(デスクトップ) を設定して、イマーシブ ヘッドセットを管理すると、ビューを公開するヘッドセット内のライブ プレビューをストリーミングします。
* **映画やテレビ**360 ビデオと最新のムービーおよび tv を表示するため次のように示しています。
* **Cortana**仮想アシスタントのすべての必要があります。
* **デスクトップ**(イマーシブ ヘッドセット)、イマーシブ ヘッドセット中のデスクトップ モニターを表示します。
* **ファイル エクスプ ローラー**ファイルと、デバイス上にあるフォルダーにアクセス

## <a name="see-also"></a>関連項目
* [アプリのビュー](app-views.md)
* [アニメーション コント ローラー](motion-controllers.md)
* [ハードウェアのアクセサリ](hardware-accessories.md)
* [HoloLens の環境に関する考慮事項](environment-considerations-for-hololens.md)
* [3D アプリ ランチャーを実装します。](implementing-3d-app-launchers.md)
* [Windows Mixed Reality 自宅で使用するための 3D モデルを作成します。](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
