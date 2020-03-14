---
title: ハードウェアのアクセサリ
description: HoloLens および Windows Mixed Reality で使用できるアクセサリの種類と、それらを設定する方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 操作方法、アクセサリ、bluetooth、bt、コントローラー、ゲームパッド、clicker、xbox
ms.openlocfilehash: 566d4217fb674057e1dc3d9791b247185bf61d32
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375699"
---
# <a name="hardware-accessories"></a>ハードウェアのアクセサリ

Windows Mixed Reality デバイスでは、アクセサリがサポートしています。 Bluetooth を使用して、サポートされているアクセサリを HoloLens にペアリングします。また、Bluetooth または USB を使用して、サポートされているアクセサリを、接続されている PC を介して、イマーシブヘッドセットにペアリングすることもできます。

HoloLens でアクセサリを使用する2つの一般的なシナリオは、エアタップジェスチャと仮想キーボードの代替として使用されます。 この場合、最も一般的な2つのアクセサリは、 **HoloLens Clicker**と**Bluetooth キーボード**です。 Microsoft HoloLens には、Bluetooth 4.1 無線が搭載されており、 [BLUETOOTH HID](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29)と[bluetooth GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29)のプロファイルをサポートしています。

Windows Mixed Reality イマーシブヘッドセットには、[宝石](gaze-and-commit.md)と[声](voice-input.md)を超えた入力のためのアクセサリが必要です。 サポートされているアクセサリには、**キーボード、マウス**、**ゲームパッド**、および **[モーションコントローラー](motion-controllers.md)** があります。

## <a name="pairing-bluetooth-accessories"></a>Bluetooth アクセサリのペアリング

Bluetooth 周辺機器と Microsoft HoloLens のペアリングは、Bluetooth 周辺機器と Windows 10 デスクトップまたはモバイルデバイスとのペアリングに似ています。
1. スタート メニューから、**設定** アプリを開きます。
2. **デバイス**にアクセス
3. Bluetooth ラジオがスライダースイッチを使用してオフになっている場合はオンにする
4. Bluetooth デバイスをペアリングモードにします。 これは、デバイスによって異なります。 ほとんどの Bluetooth デバイスでは、1つまたは複数のボタンを押したままにします。
5. デバイスの名前が Bluetooth デバイスの一覧に表示されるまで待ちます。 その場合は、デバイスを選択し、 **[ペアリング]** ボタンを選択します。 近くの Bluetooth デバイスが多数ある場合は、[Bluetooth デバイス] 一覧の一番下までスクロールして、ペアリングしようとしているデバイスを確認する必要があります。
6. Bluetooth 周辺機器と入力機能 (Bluetooth キーボードなど) をペアリングすると、6桁または8桁の pin が表示される場合があります。 周辺機器に pin を入力し、enter キーを押して、Microsoft HoloLens とのペアリングを完了してください。

## <a name="motion-controllers"></a>モーション コントローラー

Windows Mixed Reality[モーションコントローラー](motion-controllers.md)は、HoloLens ではなく、イマーシブヘッドセットでサポートされています。 これらのコントローラーは、イマーシブヘッドセットのセンサーを使用して、ビューのフィールドの移動を正確かつ迅速に追跡できます。つまり、領域内の壁にハードウェアを取り付ける必要はありません。 各コントローラーは、いくつかの入力方法を特徴としています。

![Windows Mixed Reality モーションコントローラー](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>HoloLens Clicker

HoloLens Clicker は、hololens 専用に構築された最初の周辺機器であり、HoloLens Development エディションに含まれています。 HoloLens Clicker を使用すると、ユーザーは、エアタップジェスチャの代わりとして、最小のハンドモーションでクリックしてスクロールできます。 すべての[ジェスチャ](gaze-and-commit.md#composite-gestures)に代わるものではありません。 たとえば、[ブルーム](system-gesture.md#bloom)ジェスチャや[resize](gaze-and-commit.md#composite-gestures)ジェスチャでは、ハンドモーションが使用されます。 HoloLens clicker は、単純なボタンを備えた向きセンサーデバイスです。 これは、Bluetooth 低エネルギー (BTLE) を使用して HoloLens に接続します。

![HoloLens Clicker](images/hololens-clicker-500px.jpg)

[ホログラム](hologram.md)を選択して、をクリックします。 Clicker の向きは、この操作には関係ありません。 スクロールまたはパンするには、クリックしたままにして、Clicker を上下または左右に回転させます。 スクロール中は、手首回転の速度が +/-15 °になるので、最速の速度になります。 さらに速く移動することはできません。

Clicker 内に Led が2つあります。
* 白の LED は、デバイスがペアリング (点滅) または充電 (ソリッド) であるかどうかを示します。
* 黄色の LED は、デバイスがバッテリ低下 (点滅) しているか、エラー (ソリッド) を検出したことを示します。

完全充電では2週間以上の通常の使用が予想されます (たとえば、壁チャージャーでは2-3 時間)。 バッテリが不足している場合は、ボタンを押すか、スリープ状態から復帰すると、オレンジの LED が5秒間に10回点滅します。 Clicker が非常に低バッテリモードの場合、オレンジの LED は5秒間でより速く点滅します。

## <a name="bluetooth-keyboards"></a>Bluetooth キーボード

English 言語 Qwerty Bluetooth キーボードは、holographic キーボードを使用できる任意の場所でペアにして使用できます。 品質の高いキーボードを使用すると、違いがあるため、 [Microsoft Universal たたみ込みキーボード](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001)または[Microsoft Designer Bluetooth Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)をお勧めします。

## <a name="bluetooth-gamepads"></a>Bluetooth ゲームパッド

ゲームパッドサポートを特に有効にしたアプリやゲームでコントローラーを使用できます。 ゲームパッドは、HoloLens ユーザーインターフェイスを制御するためには使用できません。

Xbox が搭載されている xbox ワイヤレスコントローラー、または xbox One のアクセサリとして販売されている xbox ワイヤレスコントローラーは、HoloLens とイマーシブヘッドセットで使用できるようにする Bluetooth 接続機能を備えています。 Xbox ワイヤレスコントローラーを HoloLens で使用するには、その前に[更新する必要があり](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)ます。

Bluetooth ゲームパッドの他のブランドは、Windows Mixed Reality デバイスで動作することがありますが、サポートはアプリケーションによって異なります。

## <a name="other-bluetooth-accessories"></a>その他の Bluetooth アクセサリ

周辺機器が Bluetooth HID または GATT のいずれかのプロファイルをサポートしている限り、HoloLens とペアリングできます。 キーボード、マウス、および HoloLens Clicker 以外の他の Bluetooth HID および GATT デバイスでは、完全に機能するためには、Microsoft HoloLens のコンパニオンアプリケーションが必要になる場合があります。

サポートされない周辺機器は次のとおりです。
* Bluetooth オーディオプロファイルの周辺機器はサポートされていません。
* Bluetooth オーディオデバイス (スピーカーやヘッドセットなど) は、設定アプリで使用できるように見える場合がありますが、オーディオエンドポイントとして Microsoft HoloLens で使用することはサポートされていません。
* Bluetooth 対応の携帯電話および Pc は、ファイル転送にペアリングして使用することはできません。

## <a name="unpairing-a-bluetooth-peripheral"></a>Bluetooth 周辺機器のペアリングを解除する
1. スタート メニューから、**設定** アプリを開きます。
2. **デバイス**にアクセス
3. Bluetooth ラジオがオフになっている場合はオンにする
4. 利用可能な Bluetooth デバイスの一覧でデバイスを検索する
5. 一覧からデバイスを選択し、 **[削除]** ボタンを選択します。

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>Microsoft HoloLens で Bluetooth を無効にする

これにより、Bluetooth ラジオの RF コンポーネントがオフになり、Microsoft HoloLens のすべての Bluetooth 機能が無効になります。
1. スタート メニューから、**設定** アプリを開きます。
2. **デバイス**にアクセス
3. Bluetooth のスライダースイッチを OFF の位置に移動する
