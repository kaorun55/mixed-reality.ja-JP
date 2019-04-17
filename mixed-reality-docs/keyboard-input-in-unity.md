---
title: Unity におけるキーボード入力
description: Unity では、使用可能な物理キーボードがない場合は、キーボード入力を受け入れるため TouchScreenKeyboard クラスを提供します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: キーボードの入力、unity、touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604888"
---
# <a name="keyboard-input-in-unity"></a>Unity におけるキーボード入力

**名前空間:***UnityEngine*<br>
 **種類**:*[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

HoloLens などの Bluetooth キーボード入力の多くの形式がサポートされますが、ほとんどのアプリケーションがすべてのユーザーが使用可能な物理キーボードにあるを想定することはできません。 アプリケーションは、テキスト入力を必要とする場合スクリーン キーボード上の何らかの形式を指定する必要があります。

Unity は、 *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 使用可能な物理キーボードがない場合は、キーボード入力を受け入れるためのクラス。

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Unity での HoloLens システム キーボード動作

HoloLens、上、 *TouchScreenKeyboard*スクリーン キーボード上のシステムを活用します。 スクリーン キーボード上のシステムは、キーボードを表示し、入力が送信された後に、帯域幅消費型のビューを返す 2D セカンダリ XAML ビューを作成するため、Unity は、帯域幅消費型ビューの上部にオーバーレイにできません。 ユーザー フローでは、次のようにします。
1. ユーザーが原因でアプリのコードを呼び出すアクションを実行*TouchScreenKeyboard*
    * アプリの呼び出しの前に、アプリの一時停止状態の役目です*TouchScreenKeyboard*
    * これまで帯域幅消費型のビューに切り替える前に終了することが、アプリ
2. Unity は、世界中の自動配置は 2D XAML ビューに切り替わります
3. ユーザーがシステム キーボードを使用してテキストを入力し、送信またはキャンセル
4. Unity は、帯域幅消費型のビューに切り替える
    * アプリを再開するため、アプリは、状態、 *TouchScreenKeyboard*は行われます
5. 送信されたテキストが表示されます、 *TouchScreenKeyboard*

### <a name="available-keyboard-views"></a>使用可能なキーボード ビュー

さまざまなキーボードの 6 つのビューを使用できます。
* 単一行のテキスト ボックス
* タイトルを含む単一行の textbox
* 複数行テキスト ボックス
* タイトルを含む複数行の textbox
* 単一行のパスワード ボックス
* 単一行のパスワード ボックスのタイトル

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Unity でシステム キーボードを有効にする方法

HoloLens システム キーボードでは、「UWP ビルドの種類」"XAML"に設定と共にエクスポートされる Unity アプリケーションで使用できるのみです。 "XAML"を「UWP ビルドの種類」として"D3D"を選択するときにすることのトレードオフがあります。 調査になる場合、これらのトレードオフに慣れていない、[ソリューションの代替入力](#alternative-keyboard-options)システム キーボードにします。
1. 開く、**ファイル**メニュー選択し、**ビルド設定しています.**
2. 確認、**プラットフォーム**に設定されている**Windows ストア**、 **SDK**に設定されている**ユニバーサル 10**、設定と、 **UWP ビルドの種類**に**XAML**します。
3. **Build Settings**ダイアログ ボックスで、をクリックして、**プレーヤー設定しています.** ボタン
4. 選択、 **Windows Store 用の設定に** タブ
5. 展開、**その他の設定**グループ
6. **レンダリング** セクションで、チェック、**仮想現実サポート**新しいを追加するチェック ボックスをオン**仮想現実デバイス**一覧
7. 確認**Windows Holographic**仮想現実 Sdk の一覧に表示されます

>[!NOTE]
>HoloLens デバイスと仮想現実のサポートとして、ビルドをマークしないで、プロジェクトは 2D XAML アプリとしてエクスポートします。

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Unity アプリでシステム キーボードの使用

### <a name="declare-the-keyboard"></a>キーボードを宣言します。

クラスを格納する変数を宣言、 *TouchScreenKeyboard*し、キーボード、文字列を保持する変数を返します。

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>キーボードを呼び出す

イベントが発生するキーボード入力を要求しているときに、必要な入力の種類に応じて、これらの関数のいずれかを呼び出します。 タイトルが textPlaceholder パラメーターで指定されたことに注意してください。

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a>型指定されたコンテンツを取得します。

Update ループでは、キーボードが新しい入力を受信するかどうか、他の場所で使用するため保存できます。

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.done == true)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a>代替キーボード オプション

切り替え元の帯域幅消費型のビューを 2D のビューに、ユーザーから入力されたテキストを取得するための望ましい方法ではないことを認識しています。

Unity からシステム キーボードを利用するための現在の代替手段は、次のとおりです。
* 入力に対して音声認識を使用して (<b>注:</b>間違いやすく、辞書で見つからなかった単語は、多くの場合、これと、パスワードの入力には適していません)
* アプリケーションのビューが排他的で動作するキーボードを作成します。
