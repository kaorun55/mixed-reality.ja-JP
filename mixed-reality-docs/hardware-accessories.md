---
title: ハードウェアのアクセサリ
description: HoloLens と Windows Mixed Reality、およびそれらを設定する方法を使用する使用可能な [アクセサリ] の種類について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 操作方法、[アクセサリ]、bluetooth、bt、コント ローラー、ゲームパッド、clicker、xbox
ms.openlocfilehash: c25f849cbf05a78ba2fe7118dbe160d05e0f5e3f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604738"
---
# <a name="hardware-accessories"></a>ハードウェアのアクセサリ

Windows Mixed Reality デバイスは、[アクセサリ] をサポートします。 Bluetooth を使用することもペアに USB に接続されている PC を使用して、イマーシブ ヘッドセットには、[アクセサリ] がサポートされているときに、Bluetooth を使用して HoloLens にサポートされている、アクセサリをペアリングします。

HoloLens で、[アクセサリ] を使用するための 2 つの一般的なシナリオでは、空気の代替のジェスチャや、仮想キーボードをタップします。 これは、2 つの最も一般的な [アクセサリ]、 **HoloLens Clicker**と**Bluetooth キーボード**します。 Microsoft HoloLens 4.1 の Bluetooth 無線が含まれていて、サポート[Bluetooth HID](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29)と[Bluetooth GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29)プロファイル。

Windows Mixed Reality イマーシブ ヘッドセット アクセサリ入力を必要とを超えて[視線](gaze.md)と[音声](voice-input.md)します。 サポートされている [アクセサリ] を含める**キーボードとマウス**、**ゲームパッド**、および**[コント ローラーのモーション](motion-controllers.md)** します。

## <a name="pairing-bluetooth-accessories"></a>Bluetooth アクセサリのペアリング

Microsoft HoloLens で Bluetooth 周辺機器をペアリングは、Windows 10 で Bluetooth 周辺機器のペアリングに似ていますデスクトップまたはモバイル デバイス。
1. [スタート] メニューから開きます、**設定**アプリ
2. 移動して**デバイス**
3. スライダーのスイッチを使用してオフになっている場合に、Bluetooth 無線をオンに
4. Bluetooth デバイスをペアリング モードで配置します。 これにより、デバイスからデバイスが異なります。 1 つまたは複数のボタンを押したままはこれがほとんどの Bluetooth デバイスで行われます。
5. Bluetooth デバイスの一覧に表示するデバイスの名前を待ちます。 デバイスを選択し、選択、ときに、**ペア**ボタンをクリックします。 ある場合を近くにある多くの Bluetooth デバイスがペアリングしようとしてデバイスを表示する Bluetooth デバイスの一覧の一番下までスクロールする必要があります。
6. 機能の Bluetooth 周辺機器をペアリング入力 (例。Bluetooth キーボードの場合)、6 桁または 8 桁の pin を表示する場合があります。 周辺機器にその pin を入力してくださいし、し、enter キーを押して、Microsoft HoloLens と完了のペアリングにします。

## <a name="motion-controllers"></a>アニメーション コント ローラー

Windows Mixed Reality[コント ローラーのモーション](motion-controllers.md)イマーシブ ヘッドセットがない HoloLens でサポートされています。 これらのコント ローラーは、つまり自分のスペースでの壁面にハードウェアをインストールする必要はありません、イマーシブ ヘッドセットのセンサーを使用して、フィールドのビューでの移動の追跡を正確かつ応答性を提供します。 各コント ローラーには、入力のいくつかの方法が機能します。

![Windows Mixed Reality モーションのコント ローラー](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>HoloLens Clicker

HoloLens Clicker HoloLens 専用に構築された最初の周辺機器、HoloLens の開発エディションに含まれています。 HoloLens Clicker をクリックして、エア タップ ジェスチャの代わりに、最小限の手の動きをスクロールできます。 すべての置換が[ジェスチャ](gestures.md)します。 たとえば、[ブルーム](gestures.md#bloom)と[サイズ変更または移動](gestures.md#composite-gestures)ジェスチャが手の動きを使用します。 HoloLens clicker は、単純なボタンで方向センサー デバイスです。 これは、Bluetooth 低エネルギー (BTLE) を使用して、HoloLens に接続します。

![HoloLens Clicker](images/hololens-clicker-500px.jpg)

選択する、[ホログラム](hologram.md)見つめますをクリックします。 この操作には、clicker の方向は関係ありません。 スクロール、パンまたはクリックし、ながらを回転させて、Clicker 上下または左右します。 スクロール時に、最も速い速度で 15 ° 手首回転の +/-わずかに到達します。 移動の詳細はしないスクロールいずれかの高速化します。

これには、Clicker 内の 2 つの Led があります。
* 白の LED は、(点滅) デバイスをペアリングするかどうかを示しますまたは充電 (ソリッド)
* アンバー色の LED は、デバイスがバッテリ (点滅) または (ソリッド) エラーが発生したことを示します

完全充電状態 (つまり、壁の充電器で 2 ~ 3 時間) は、2 週間以上の正規表現の使用を想定できます。 バッテリが少ない場合、オレンジの場合は、ボタンを押すか、スリープ状態から復帰させると、5 秒間に 10 回 LED が点滅します。 バッテリが著しく低下モードでは、Clicker をアンバー色のより迅速に 5 秒間の期間の場合に LED が点滅します。

## <a name="bluetooth-keyboards"></a>Bluetooth キーボード

英語 Qwerty Bluetooth キーボードを使用して、対ことができます、holographic のキーボードを使用する任意の場所を使用します。 品質キーボードが差を取得して、これをお勧め、 [Microsoft ユニバーサルたたみ込み可能なキーボード](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001)または[Microsoft デザイナー Bluetooth Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)します。

## <a name="bluetooth-gamepads"></a>Bluetooth ゲームパッド

具体的にはゲームパッド サポートを有効にするアプリおよびゲームでは、コント ローラーを使用できます。 HoloLens のユーザー インターフェイスを制御する、ゲーム パッドを使用できません。

Xbox の 1 つの S または HoloLens とイマーシブ ヘッドセットで使用できるようになります、Xbox の 1 つの機能の Bluetooth 接続のアクセサリとして販売ある Xbox のワイヤレス コント ローラー Xbox のワイヤレス コント ローラー[更新する必要があります](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)前に、HoloLens のために使用できます。

Windows Mixed Reality のデバイスで Bluetooth ゲームパッドの他のブランドが動作しますが、サポートはアプリケーションによって異なります。

## <a name="other-bluetooth-accessories"></a>その他の Bluetooth アクセサリ

周辺機器に Bluetooth HID または GATT プロファイルをサポートしている限りは、HoloLens とペアにすることはできます。 キーボード、マウス、および HoloLens Clicker だけでなく、その他の Bluetooth を非表示にし、GATT のデバイスには、完全に機能するために Microsoft HoloLens のコンパニオン アプリケーションを必要があります。

サポートされていない周辺機器は次のとおりです。
* Bluetooth のオーディオ プロファイルの周辺機器がサポートされていません。
* Bluetooth スピーカーやヘッドセットなどのオーディオ デバイスは、設定アプリで利用可能な場合がありますが、Microsoft HoloLens でオーディオのエンドポイントとして使用することはできません。
* ペアになっているし、ファイル転送に使用するのには、Bluetooth 対応のスマート フォンや Pc がサポートされていません。

## <a name="unpairing-a-bluetooth-peripheral"></a>Bluetooth 周辺機器のペアリングを解除
1. [スタート] メニューから開きます、**設定**アプリ
2. 移動して**デバイス**
3. オフになっている場合に、Bluetooth 無線をオンに
4. 使用可能な Bluetooth デバイスの一覧で、デバイスが見つかりません
5. 一覧から、デバイスを選択し、、**削除**ボタン

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>Microsoft HoloLens で Bluetooth を無効にします。

Bluetooth 無線の RF コンポーネントをオフにされ Microsoft HoloLens ですべての Bluetooth 機能を無効にします。
1. [スタート] メニューから開きます、**設定**アプリ
2. 移動して**デバイス**
3. Bluetooth のスライダーのスイッチを OFF の位置に移動します。
