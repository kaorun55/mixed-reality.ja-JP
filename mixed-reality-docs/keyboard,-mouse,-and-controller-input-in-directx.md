---
title: キーボード、マウス、および DirectX でコント ローラーの入力
description: キーボード、マウス、およびゲーム コント ローラーを使用する Windows Mixed Reality アプリを作成する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、キーボード、マウス、ゲーム コント ローラー、HoloLens、xbox コント ローラーで、デスクトップ、チュートリアル、サンプル コード
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605088"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>キーボード、マウス、および DirectX でコント ローラーの入力

キーボード、マウス、およびゲーム コント ローラーすべて Windows Mixed Reality デバイス用の入力の便利なフォームを指定できます。 Bluetooth キーボードとマウスの両方がサポート、HoloLens でアプリのデバッグで、または、代替形式の入力として使用します。 Windows Mixed Reality は、マウス、キーボード、およびゲーム コント ローラーとなってきた、norm - Pc に接続されている、イマーシブ ヘッドセットもサポートします。

HoloLens、ペアに、デバイスの Bluetooth キーボードでキーボード入力を使用して、または、Windows Device Portal を使用して、仮想入力を使用します。 Windows Mixed Reality イマーシブ ヘッドセット ソックスを着けずにいるときにキーボード入力を使用するには、デバイスに配置するか、Windows キー + Y キーの組み合わせを使用して、複合現実に入力フォーカスを割り当てます。 HoloLens の対象としたアプリが接続されているこれらのデバイスなし機能を提供する必要がありますに留意してください。

>[!NOTE]
>この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。  概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。

## <a name="subscribe-for-corewindow-input-events"></a>CoreWindow 入力イベントをサブスクライブします。

### <a name="keyboard-input"></a>キーボード入力

Windows Holographic のアプリケーション テンプレートで他の UWP アプリと同じようにキーボード入力のイベント ハンドラーが含まれます。 アプリは、Windows Mixed Reality で同じようにキーボード入力データを消費します。

AppView.cpp: から

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a>仮想キーボード入力
没入型のデスクトップ ヘッドセットには、Windows によって、没入型のビューに表示される仮想キーボードもサポートできます。 これをサポートするアプリを実装できます**CoreTextEditContext**します。 これには、Windows 仮想キーボード正しくテキストが参加できるように、アプリ側でレンダリングされるテキスト ボックスの状態を理解することができます。

CoreTextEditContext サポートの実装の詳細については、次を参照してください。、 [CoreTextEditContext サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)します。

### <a name="mouse-input"></a>マウス入力

UWP CoreWindow 入力イベントのハンドラーを使用してもう一度、マウスの入力を使用することもできます。 同じように押されたジェスチャでマウスのクリックをサポートするために、Windows Holographic のアプリケーション テンプレートを変更する方法を次に示します。 したらこの変更は、イマーシブ ヘッドセット デバイスを装着しているときにマウスのクリックにキューブが再配置します。

サイト サーバー、UWP アプリできますを使用して、マウスの生データはお客様 xy のところを取得します。 に注意してください、 [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API。

AppView.h で新しい OnPointerPressed ハンドラーを宣言することで開始します。

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

AppView.cpp では、SetWindow にこのコードを追加します。

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

ファイルの下部にある OnPointerPressed のこの定義を配置します。

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

イベント ハンドラーを追加しましたが、テンプレートの主なクラスに、パススルーします。 このパススルーをサポートするために、メイン クラスを変更してみましょう。 ヘッダー ファイルには、このパブリック メソッドの宣言を追加します。

```
// Handle mouse input.
       void OnPointerPressed();
```

このプライベート メンバー変数も必要があります。

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

最後に、メイン クラスのマウス クリックをサポートする新しいロジックと共に更新されます。 このイベント ハンドラーを追加することで開始します。 クラス名を更新してください。

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

ここで、Update メソッドでは、このポインターの姿勢を取得するための既存のロジックを置き換えます。

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

再コンパイルし、再デプロイします。 マウス クリックがようになりましたの位置を変更、キューブには、HoloLens、イマーシブ ヘッドセット - bluetooth マウスが接続されているとすることがわかります。

### <a name="game-controller-support"></a>ゲーム コント ローラーのサポート

ゲーム コント ローラーには、楽しく魅力的な Windows Mixed Reality エクスペリエンスを制御するユーザーを許可する際の便利な方法を指定できます。

ゲーム コント ローラーのサポートを Windows Holographic のアプリ テンプレートに追加するのには、最初の手順では、メインのファイルのヘッダーのクラスに次のプライベート メンバー宣言を追加します。

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

Gamepad イベント、および現在接続されている、主要なクラスのコンス トラクターで、ゲームパッドを初期化します。

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

メイン クラスには、これらのイベント ハンドラーを追加します。 クラス名を更新してください。

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

最後に、コント ローラーの状態の変更を認識する入力のロジックを更新します。 ここでは、マウス イベントを追加するため、上のセクションで説明した同じ m_pointerPressed 変数を使用します。 SpatialPointerPose をチェックする前に、Update メソッドを追加します。

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

メイン クラスをクリーンアップする場合、イベントの登録を解除することを忘れないでください。

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

再コンパイルして再デプロイします。 アタッチ、ゲーム コント ローラーとペアにまたはとそれを使用して、回転するキューブの位置を変更するようになりましたことができます。

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>キーボードとマウス入力に関する重要なガイドライン

Microsoft HoloLens – これは主に Windows Mixed Reality 対応の PC で使用できると – 自然なユーザー入力に依存しているデバイス上のこのコードの使用方法の主な相違点があります。
* キーボードまたはマウスが存在する入力を利用できません。 すべてのアプリの機能は、視線、ジェスチャ、音声入力と作業する必要があります。
* Bluetooth キーボードが接続されている場合は、アプリがありますを要求する任意のテキストのキーボード入力を有効にすると便利ができます。 たとえば、音声入力の優れた追加条項を指定できます。
* アプリを設計する際、WASD (など) に依存しないようにし、マウスがゲームのコントロールを検索します。 HoloLens は、ルームまでわざわざ行かずに、ユーザーに適しています。 この場合、ユーザーは、カメラを直接制御します。 移動/参照コントロールで部屋のカメラを促進するためのインターフェイスには、同じエクスペリエンスを提供しません。
* キーボード入力には、ユーザーがキーボードを使用する必要はありませんので特にアプリやゲームのエンジンのデバッグの側面を制御する優れた方法を指定できます。 接続には、同じ as CoreWindow イベント Api で、使用しているです。 このシナリオでは、デバッグ セッション中に"debug 入力専用"モードにキーボード イベントをルーティングするアプリを構成する方法を実装することもできます。
* Bluetooth コント ローラーがうまく動作します。

## <a name="see-also"></a>関連項目
* [ハードウェアのアクセサリ](hardware-accessories.md)
