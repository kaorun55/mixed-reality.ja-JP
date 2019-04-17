---
title: Windows Mixed Reality シミュレーターの使用
description: Windows Mixed Reality シミュレーターでは、Windows Mixed Reality イマーシブ ヘッドセットなし、PC 上の複合現実アプリをテストできます。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows の混合実際には、シミュレーターのテスト
ms.openlocfilehash: 782cab85f163edd2afc4251210b7596c73dcc8b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603637"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Windows Mixed Reality シミュレーターの使用

Windows Mixed Reality シミュレーターでは、Windows Mixed Reality イマーシブ ヘッドセットなし、PC 上の複合現実アプリをテストできます。 以降、Windows 10 Creators Update で利用可能になります。 シミュレーターと似ています、 [HoloLens のエミュレーター](using-the-hololens-emulator.md)できたとして、シミュレーターは、仮想マシンを使用しません。 シミュレーターで実行されているアプリは、イマーシブ ヘッドセットを使用していた場合と同様、Windows 10 デスクトップ ユーザーのセッションで実行します。 通常、イマーシブ ヘッドセットのセンサーによって読み取られる人間と環境の入力は、キーボード、マウス、または Xbox コント ローラーを使用して代わりにシミュレートします。 アプリでは、シミュレーターで実行するように変更する必要はありませんをイマーシブ ヘッドセットで実行されていないことがわからない。

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Windows Mixed Reality シミュレーターを有効にします。

1. **開発者モードを有効にする**設定から]、[更新とセキュリティは、開発者向け]-> [
2. 起動、 **Mixed Reality ポータル**デスクトップから
3. 初めてポータルを起動する場合は、セットアップ エクスペリエンスを経由する必要があります。
   1. クリックして**を開始します。**
   2. クリックして**同意**契約に同意するには
   3. クリックして**シミュレーション (開発者) を設定する**物理デバイスがなくてもセットアップを続行するには
   4. クリックして**セットアップ**を確定するには
4. をクリックして、**開発者向け**Mixed Reality ポータルの左側にあるボタンをクリックします。
5. シミュレーションのトグル スイッチを有効に**で**
   * Admin アクセス許可が必要であり、表示されるユーザー アカウント制御ダイアログを受け入れる必要があります。

今すぐ、シミュレーションを実行する必要があります!

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Mixed Reality シミュレーターにアプリを展開します。

ユニバーサル Windows アプリをデプロイするため、シミュレーターを実行せず、仮想マシンのローカル コンピューター上だけことができます、**ローカル マシン**をデバッグするとき。

## <a name="basic-simulator-input"></a>基本的なシミュレーターの入力

多くの一般的な 3 D ビデオ ゲームによく似ていますが、シミュレーターを制御して、 [HoloLens のエミュレーター](using-the-hololens-emulator.md)します。 入力オプションは、キーボード、マウス、または Xbox コント ローラーを使用できます。

シミュレーターを制御するには、ソックスを着けずに、イマーシブ ヘッドセット シミュレートされたユーザーの操作を送信します。 操作は、シミュレートされたユーザーを移動し、応答、イマーシブ ヘッドセットの場合とするアプリとのやり取りが発生します。
* **転送で、左、について説明し、右**-、W を使用して、キーボード、または Xbox コント ローラーでは、左側のスティック A、S、D キー。
* **検索、下、左、および右**-キーボード、または Xbox コント ローラーでは、適切なスティック上方向キーを使用 をクリックし、マウスをドラッグします。
* **コント ローラーのアクション ボタンを押す**- マウスを右クリックし、キーボードの Enter キーを押してまたは Xbox コント ローラーでは、[A] ボタンを使用します。
* **ホーム コント ローラー上のボタンを押す**- には、キーボードの Windows キーまたは F2 キーを押して、または Xbox コント ローラーの B ボタンを押します。
* **スクロールのためにコント ローラー移動**- Alt キーを押しながらマウスの右ボタンを押しながらとアップ/ダウン、マウスをドラッグまたは Xbox コント ローラーで、適切なトリガーとボタンを押し、適切なスティックを上下に移動します。

## <a name="tracked-controllers"></a>追跡コント ローラー

Mixed Reality シミュレーターでは、最大で 2 つのハンドヘルド履歴モーション コント ローラーをシミュレートできます。 Mixed Reality ポータルのトグル スイッチを使用して有効にします。 シミュレートされた各コント ローラーがあります。
* 空間内の位置
* [ホーム] ボタン
* メニュー ボタン
* グリップのボタン
* タッチパッド

## <a name="see-also"></a>関連項目
* [HoloLens のエミュレーターを使用する](using-the-hololens-emulator.md)
* [Mixed Reality シミュレーターの入力を高度な](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Unity での空間のマッピング](spatial-mapping-in-unity.md)
* [DirectX での空間のマッピング](spatial-mapping-in-directx.md)
