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
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="86f37-104">キーボード、マウス、および DirectX でコント ローラーの入力</span><span class="sxs-lookup"><span data-stu-id="86f37-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="86f37-105">キーボード、マウス、およびゲーム コント ローラーすべて Windows Mixed Reality デバイス用の入力の便利なフォームを指定できます。</span><span class="sxs-lookup"><span data-stu-id="86f37-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="86f37-106">Bluetooth キーボードとマウスの両方がサポート、HoloLens でアプリのデバッグで、または、代替形式の入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="86f37-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="86f37-107">Windows Mixed Reality は、マウス、キーボード、およびゲーム コント ローラーとなってきた、norm - Pc に接続されている、イマーシブ ヘッドセットもサポートします。</span><span class="sxs-lookup"><span data-stu-id="86f37-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="86f37-108">HoloLens、ペアに、デバイスの Bluetooth キーボードでキーボード入力を使用して、または、Windows Device Portal を使用して、仮想入力を使用します。</span><span class="sxs-lookup"><span data-stu-id="86f37-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="86f37-109">Windows Mixed Reality イマーシブ ヘッドセット ソックスを着けずにいるときにキーボード入力を使用するには、デバイスに配置するか、Windows キー + Y キーの組み合わせを使用して、複合現実に入力フォーカスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="86f37-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="86f37-110">HoloLens の対象としたアプリが接続されているこれらのデバイスなし機能を提供する必要がありますに留意してください。</span><span class="sxs-lookup"><span data-stu-id="86f37-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="86f37-111">この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。</span><span class="sxs-lookup"><span data-stu-id="86f37-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="86f37-112">概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86f37-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="86f37-113">CoreWindow 入力イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="86f37-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="86f37-114">キーボード入力</span><span class="sxs-lookup"><span data-stu-id="86f37-114">Keyboard input</span></span>

<span data-ttu-id="86f37-115">Windows Holographic のアプリケーション テンプレートで他の UWP アプリと同じようにキーボード入力のイベント ハンドラーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="86f37-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="86f37-116">アプリは、Windows Mixed Reality で同じようにキーボード入力データを消費します。</span><span class="sxs-lookup"><span data-stu-id="86f37-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="86f37-117">AppView.cpp: から</span><span class="sxs-lookup"><span data-stu-id="86f37-117">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="86f37-118">仮想キーボード入力</span><span class="sxs-lookup"><span data-stu-id="86f37-118">Virtual keyboard input</span></span>
<span data-ttu-id="86f37-119">没入型のデスクトップ ヘッドセットには、Windows によって、没入型のビューに表示される仮想キーボードもサポートできます。</span><span class="sxs-lookup"><span data-stu-id="86f37-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="86f37-120">これをサポートするアプリを実装できます**CoreTextEditContext**します。</span><span class="sxs-lookup"><span data-stu-id="86f37-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="86f37-121">これには、Windows 仮想キーボード正しくテキストが参加できるように、アプリ側でレンダリングされるテキスト ボックスの状態を理解することができます。</span><span class="sxs-lookup"><span data-stu-id="86f37-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="86f37-122">CoreTextEditContext サポートの実装の詳細については、次を参照してください。、 [CoreTextEditContext サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)します。</span><span class="sxs-lookup"><span data-stu-id="86f37-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="86f37-123">マウス入力</span><span class="sxs-lookup"><span data-stu-id="86f37-123">Mouse Input</span></span>

<span data-ttu-id="86f37-124">UWP CoreWindow 入力イベントのハンドラーを使用してもう一度、マウスの入力を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="86f37-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="86f37-125">同じように押されたジェスチャでマウスのクリックをサポートするために、Windows Holographic のアプリケーション テンプレートを変更する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="86f37-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="86f37-126">したらこの変更は、イマーシブ ヘッドセット デバイスを装着しているときにマウスのクリックにキューブが再配置します。</span><span class="sxs-lookup"><span data-stu-id="86f37-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="86f37-127">サイト サーバー、UWP アプリできますを使用して、マウスの生データはお客様 xy のところを取得します。 に注意してください、 [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API。</span><span class="sxs-lookup"><span data-stu-id="86f37-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="86f37-128">AppView.h で新しい OnPointerPressed ハンドラーを宣言することで開始します。</span><span class="sxs-lookup"><span data-stu-id="86f37-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="86f37-129">AppView.cpp では、SetWindow にこのコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="86f37-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="86f37-130">ファイルの下部にある OnPointerPressed のこの定義を配置します。</span><span class="sxs-lookup"><span data-stu-id="86f37-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="86f37-131">イベント ハンドラーを追加しましたが、テンプレートの主なクラスに、パススルーします。</span><span class="sxs-lookup"><span data-stu-id="86f37-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="86f37-132">このパススルーをサポートするために、メイン クラスを変更してみましょう。</span><span class="sxs-lookup"><span data-stu-id="86f37-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="86f37-133">ヘッダー ファイルには、このパブリック メソッドの宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="86f37-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="86f37-134">このプライベート メンバー変数も必要があります。</span><span class="sxs-lookup"><span data-stu-id="86f37-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="86f37-135">最後に、メイン クラスのマウス クリックをサポートする新しいロジックと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="86f37-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="86f37-136">このイベント ハンドラーを追加することで開始します。</span><span class="sxs-lookup"><span data-stu-id="86f37-136">Start by adding this event handler.</span></span> <span data-ttu-id="86f37-137">クラス名を更新してください。</span><span class="sxs-lookup"><span data-stu-id="86f37-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="86f37-138">ここで、Update メソッドでは、このポインターの姿勢を取得するための既存のロジックを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="86f37-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="86f37-139">再コンパイルし、再デプロイします。</span><span class="sxs-lookup"><span data-stu-id="86f37-139">Recompile and redeploy.</span></span> <span data-ttu-id="86f37-140">マウス クリックがようになりましたの位置を変更、キューブには、HoloLens、イマーシブ ヘッドセット - bluetooth マウスが接続されているとすることがわかります。</span><span class="sxs-lookup"><span data-stu-id="86f37-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="86f37-141">ゲーム コント ローラーのサポート</span><span class="sxs-lookup"><span data-stu-id="86f37-141">Game controller support</span></span>

<span data-ttu-id="86f37-142">ゲーム コント ローラーには、楽しく魅力的な Windows Mixed Reality エクスペリエンスを制御するユーザーを許可する際の便利な方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="86f37-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="86f37-143">ゲーム コント ローラーのサポートを Windows Holographic のアプリ テンプレートに追加するのには、最初の手順では、メインのファイルのヘッダーのクラスに次のプライベート メンバー宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="86f37-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="86f37-144">Gamepad イベント、および現在接続されている、主要なクラスのコンス トラクターで、ゲームパッドを初期化します。</span><span class="sxs-lookup"><span data-stu-id="86f37-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="86f37-145">メイン クラスには、これらのイベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="86f37-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="86f37-146">クラス名を更新してください。</span><span class="sxs-lookup"><span data-stu-id="86f37-146">Make sure to update the class name:</span></span>

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

<span data-ttu-id="86f37-147">最後に、コント ローラーの状態の変更を認識する入力のロジックを更新します。</span><span class="sxs-lookup"><span data-stu-id="86f37-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="86f37-148">ここでは、マウス イベントを追加するため、上のセクションで説明した同じ m_pointerPressed 変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="86f37-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="86f37-149">SpatialPointerPose をチェックする前に、Update メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="86f37-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="86f37-150">メイン クラスをクリーンアップする場合、イベントの登録を解除することを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="86f37-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="86f37-151">再コンパイルして再デプロイします。</span><span class="sxs-lookup"><span data-stu-id="86f37-151">Recompile, and redeploy.</span></span> <span data-ttu-id="86f37-152">アタッチ、ゲーム コント ローラーとペアにまたはとそれを使用して、回転するキューブの位置を変更するようになりましたことができます。</span><span class="sxs-lookup"><span data-stu-id="86f37-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="86f37-153">キーボードとマウス入力に関する重要なガイドライン</span><span class="sxs-lookup"><span data-stu-id="86f37-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="86f37-154">Microsoft HoloLens – これは主に Windows Mixed Reality 対応の PC で使用できると – 自然なユーザー入力に依存しているデバイス上のこのコードの使用方法の主な相違点があります。</span><span class="sxs-lookup"><span data-stu-id="86f37-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="86f37-155">キーボードまたはマウスが存在する入力を利用できません。</span><span class="sxs-lookup"><span data-stu-id="86f37-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="86f37-156">すべてのアプリの機能は、視線、ジェスチャ、音声入力と作業する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86f37-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="86f37-157">Bluetooth キーボードが接続されている場合は、アプリがありますを要求する任意のテキストのキーボード入力を有効にすると便利ができます。</span><span class="sxs-lookup"><span data-stu-id="86f37-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="86f37-158">たとえば、音声入力の優れた追加条項を指定できます。</span><span class="sxs-lookup"><span data-stu-id="86f37-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="86f37-159">アプリを設計する際、WASD (など) に依存しないようにし、マウスがゲームのコントロールを検索します。</span><span class="sxs-lookup"><span data-stu-id="86f37-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="86f37-160">HoloLens は、ルームまでわざわざ行かずに、ユーザーに適しています。</span><span class="sxs-lookup"><span data-stu-id="86f37-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="86f37-161">この場合、ユーザーは、カメラを直接制御します。</span><span class="sxs-lookup"><span data-stu-id="86f37-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="86f37-162">移動/参照コントロールで部屋のカメラを促進するためのインターフェイスには、同じエクスペリエンスを提供しません。</span><span class="sxs-lookup"><span data-stu-id="86f37-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="86f37-163">キーボード入力には、ユーザーがキーボードを使用する必要はありませんので特にアプリやゲームのエンジンのデバッグの側面を制御する優れた方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="86f37-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="86f37-164">接続には、同じ as CoreWindow イベント Api で、使用しているです。</span><span class="sxs-lookup"><span data-stu-id="86f37-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="86f37-165">このシナリオでは、デバッグ セッション中に"debug 入力専用"モードにキーボード イベントをルーティングするアプリを構成する方法を実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="86f37-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="86f37-166">Bluetooth コント ローラーがうまく動作します。</span><span class="sxs-lookup"><span data-stu-id="86f37-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="86f37-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="86f37-167">See also</span></span>
* [<span data-ttu-id="86f37-168">ハードウェアのアクセサリ</span><span class="sxs-lookup"><span data-stu-id="86f37-168">Hardware accessories</span></span>](hardware-accessories.md)
