---
title: 視線、ジェスチャ、および DirectX でモーション コント ローラー
description: 視線、ジェスチャ、およびモーションのコント ローラーからの入力の受信を組み合わせると、アプリでホログラムを配置するユーザーを有効にできます。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 視線、ジェスチャ、アニメーション コント ローラー、directx、入力、ホログラム
ms.openlocfilehash: 7cee3d3d7fbcd903eae0376e205034b9cc4ead3b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605091"
---
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a><span data-ttu-id="c9492-104">視線、ジェスチャ、および DirectX でモーション コント ローラー</span><span class="sxs-lookup"><span data-stu-id="c9492-104">Gaze, gestures, and motion controllers in DirectX</span></span>

<span data-ttu-id="c9492-105">プラットフォーム上に直接構築しようとしているなどを使用して、ユーザーを検索する場所のユーザーからの入力の受信を処理する必要があります[ヘッド注視](gaze.md)ユーザーがの選択と[ジェスチャ](gestures.md)または[コント ローラーのモーション](motion-controllers.md)します。</span><span class="sxs-lookup"><span data-stu-id="c9492-105">If you're going to build directly on top of the platform, you will have to handle input coming from the user - such as where the user is looking via [head gaze](gaze.md) and what the user has selected with [gestures](gestures.md) or [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="c9492-106">これらのフォームの入力を組み合わせると、配置するユーザーを有効ことができます、[ホログラム](hologram.md)アプリ。</span><span class="sxs-lookup"><span data-stu-id="c9492-106">Combining these forms of input, you can enable a user to place a [hologram](hologram.md) in your app.</span></span> <span data-ttu-id="c9492-107">[Holographic アプリ テンプレート](creating-a-holographic-directx-project.md)使いやすい例があります。</span><span class="sxs-lookup"><span data-stu-id="c9492-107">The [holographic app template](creating-a-holographic-directx-project.md) has an easy to use example.</span></span>

>[!NOTE]
><span data-ttu-id="c9492-108">この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。</span><span class="sxs-lookup"><span data-stu-id="c9492-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="c9492-109">概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9492-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="gaze-input"></a><span data-ttu-id="c9492-110">視線入力</span><span class="sxs-lookup"><span data-stu-id="c9492-110">Gaze input</span></span>

<span data-ttu-id="c9492-111">ユーザーのアクセスに[ヘッド注視](gaze.md)を使用する、 [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx)型。</span><span class="sxs-lookup"><span data-stu-id="c9492-111">To access the user's [head gaze](gaze.md), you use the [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) type.</span></span> <span data-ttu-id="c9492-112">Holographic アプリ テンプレートには、視線の先についての基本的なコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c9492-112">The holographic app template includes basic code for understanding gaze.</span></span> <span data-ttu-id="c9492-113">このコードにより、ユーザーの視点で、デバイスの位置と向きを考慮して書き込むフォワード ポイント ベクター、特定[座標系](coordinate-systems-in-directx.md)します。</span><span class="sxs-lookup"><span data-stu-id="c9492-113">This code provides a vector pointing forward from between the user's eyes, taking into account the device's position and orientation in a given [coordinate system](coordinate-systems-in-directx.md).</span></span>




```cpp
void SpinningCubeRenderer::PositionHologram(SpatialPointerPose^ pointerPose)
{
    if (pointerPose != nullptr)
    {
        // Get the gaze direction relative to the given coordinate system.
        const float3 headPosition    = pointerPose->Head->Position;
        const float3 headDirection   = pointerPose->Head->ForwardDirection;
    
        // The hologram is positioned two meters along the user's gaze direction.
        static const float distanceFromUser = 2.0f; // meters
        const float3 gazeAtTwoMeters        = headPosition + (distanceFromUser * headDirection);
    
        // This will be used as the translation component of the hologram's
        // model transform.
        SetPosition(gazeAtTwoMeters);
    }
}
```

<span data-ttu-id="c9492-114">なぜかを見つけることがあります。「しかし座標系はどこからでしょうか。」</span><span class="sxs-lookup"><span data-stu-id="c9492-114">You may find yourself asking: "But where does the coordinate system come from?"</span></span>

<span data-ttu-id="c9492-115">質問にお答えしておきましょう。</span><span class="sxs-lookup"><span data-stu-id="c9492-115">Let's answer that question.</span></span> <span data-ttu-id="c9492-116">AppMain の**Update**関数、StationaryFrameOfReference 用の座標系を基準と取得することによって空間の入力イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="c9492-116">In our AppMain's **Update** function, we processed a spatial input event by acquiring it relative to the coordinate system for our StationaryFrameOfReference.</span></span> <span data-ttu-id="c9492-117">設定するときに、StationaryFrameOfReference が作成されたことを思い出してください、 [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)、座標システムの起動時に取得され[Update](rendering-in-directx.md)します。</span><span class="sxs-lookup"><span data-stu-id="c9492-117">Recall that the StationaryFrameOfReference was created when we set up the [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), and the coordinate system was acquired at the start of [Update](rendering-in-directx.md).</span></span>




```cpp
// Check for new input state since the last frame.
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
if (pointerState != nullptr)
{
    // When a Pressed gesture is detected, the sample hologram will be repositioned
    // two meters in front of the user.
    m_spinningCubeRenderer->PositionHologram(
        pointerState->TryGetPointerPose(currentCoordinateSystem)
        );
}
```

<span data-ttu-id="c9492-118">データはある種のポインターの状態に関連付けられていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c9492-118">Note that the data is tied to a pointer state of some kind.</span></span> <span data-ttu-id="c9492-119">私たちは空間の入力イベントからこれを取得します。</span><span class="sxs-lookup"><span data-stu-id="c9492-119">We get this from a spatial input event.</span></span> <span data-ttu-id="c9492-120">イベント データ オブジェクトには、するため、必要な空間座標系を常に、イベントの時点で視線方向を関連付けることができます、座標系が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c9492-120">The event data object includes a coordinate system, so that you can always relate the gaze direction at the time of the event to whatever spatial coordinate system you need.</span></span> <span data-ttu-id="c9492-121">実際には、これをポインター姿勢を取得するために行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9492-121">In fact, you must do so in order to get the pointer pose.</span></span>

> [!NOTE]
> <span data-ttu-id="c9492-122">HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。</span><span class="sxs-lookup"><span data-stu-id="c9492-122">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="gesture-and-motion-controller-input"></a><span data-ttu-id="c9492-123">ジェスチャとアニメーション コント ローラーの入力</span><span class="sxs-lookup"><span data-stu-id="c9492-123">Gesture and motion controller input</span></span>

<span data-ttu-id="c9492-124">Windows Mixed Reality でどちらも渡す[ジェスチャ](gestures.md)と[コント ローラーのモーション](motion-controllers.md)にある同じ空間入力 Api によって処理されます、 [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)名前空間。</span><span class="sxs-lookup"><span data-stu-id="c9492-124">In Windows Mixed Reality, both hand [gestures](gestures.md) and [motion controllers](motion-controllers.md) are handled through the same spatial input APIs, found in the [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) namespace.</span></span> <span data-ttu-id="c9492-125">などの一般的なアクションを簡単に処理できます**選択**ハンドとアニメーション コント ローラーの両方で同じ方法を押します。</span><span class="sxs-lookup"><span data-stu-id="c9492-125">This enables you to easily handle common actions like **Select** presses the same way across both hands and motion controllers.</span></span>

<span data-ttu-id="c9492-126">複合現実でジェスチャやアニメーション コント ローラーを処理するときに対象にできます API の 2 つのレベルです。</span><span class="sxs-lookup"><span data-stu-id="c9492-126">There are two levels of API you can target when handling gestures or motion controllers in mixed reality:</span></span>
* <span data-ttu-id="c9492-127">[相互作用](gestures.md#the-two-core-gestures-of-hololens)([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx)、 [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx)と[SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)) を使用してアクセスされる、 [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span><span class="sxs-lookup"><span data-stu-id="c9492-127">[Interactions](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) and [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), accessed using a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span></span>
* <span data-ttu-id="c9492-128">[複合ジェスチャ](gestures.md#composite-gestures)([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx)、保持、操作、ナビゲーション) を使用してアクセスされる、 [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span><span class="sxs-lookup"><span data-stu-id="c9492-128">[Composite gestures](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), Hold, Manipulation, Navigation), accessed using a [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span></span>

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a><span data-ttu-id="c9492-129">選択/メニュー/理解/タッチパッド/スティックの相互作用:SpatialInteractionManager</span><span class="sxs-lookup"><span data-stu-id="c9492-129">Select/Menu/Grasp/Touchpad/Thumbstick interactions: SpatialInteractionManager</span></span>

<span data-ttu-id="c9492-130">起動する手と Windows Mixed Reality で入力デバイスの間で低レベルの押下、リリースと更新プログラムを検出するために、 [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)します。</span><span class="sxs-lookup"><span data-stu-id="c9492-130">To detect low-level presses, releases and updates across hands and input devices in Windows Mixed Reality, you start from a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span></span> <span data-ttu-id="c9492-131">SpatialInteractionManager が手の形のときに、アプリに通知するイベントまたはアニメーション コント ローラーが入力を検出します。</span><span class="sxs-lookup"><span data-stu-id="c9492-131">The SpatialInteractionManager has an event that informs the app when a hand or motion controller has detected input.</span></span>

<span data-ttu-id="c9492-132">SpatialInteractionSource の 3 のキーの種類は、それぞれ異なる SpatialInteractionSourceKind 値で表されます。</span><span class="sxs-lookup"><span data-stu-id="c9492-132">There are three key kinds of SpatialInteractionSource, each represented by a different SpatialInteractionSourceKind value:</span></span>
* <span data-ttu-id="c9492-133">**ハンド**検出されたユーザーの手の形を表します。</span><span class="sxs-lookup"><span data-stu-id="c9492-133">**Hand** represents a user's detected hand.</span></span> <span data-ttu-id="c9492-134">手動のソースは、HoloLens でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c9492-134">Hand sources are available only on HoloLens.</span></span>
* <span data-ttu-id="c9492-135">**コント ローラー**ペアになっているアニメーション コント ローラーを表します。</span><span class="sxs-lookup"><span data-stu-id="c9492-135">**Controller** represents a paired motion controller.</span></span> <span data-ttu-id="c9492-136">モーションのコント ローラーは、たとえば、機能のさまざまなを提供できます。トリガー、メニュー ボタン、ボタンの把握、タッチパッドおよびサムスティックを選択します。</span><span class="sxs-lookup"><span data-stu-id="c9492-136">Motion controllers can offer a variety of capabilities, for example: Select triggers, Menu buttons, Grasp buttons, touchpads and thumbsticks.</span></span>
* <span data-ttu-id="c9492-137">**音声**システム検出キーワードを言うと、ユーザーの音声を表します。</span><span class="sxs-lookup"><span data-stu-id="c9492-137">**Voice** represents the user's voice speaking system-detected keywords.</span></span> <span data-ttu-id="c9492-138">キーを押して挿入され、ユーザーは、"Select"が話すたびにリリースされます。</span><span class="sxs-lookup"><span data-stu-id="c9492-138">This will inject a Select press and release whenever the user says "Select".</span></span>

<span data-ttu-id="c9492-139">押す間でこれらの操作のソースのいずれかを検出するには、SpatialInputHandler.cpp で SpatialInteractionManager で SourcePressed イベントを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="c9492-139">To detect presses across any of these interaction sources, you can handle the SourcePressed event on SpatialInteractionManager in SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

<span data-ttu-id="c9492-140">押されたこのイベントは、アプリに非同期的に送信されます。</span><span class="sxs-lookup"><span data-stu-id="c9492-140">This pressed event is sent to your app asynchronously.</span></span> <span data-ttu-id="c9492-141">アプリやゲーム エンジンはすぐに、いくつか処理を実行することがあります。 またはルーチンを処理する、入力イベント データをキューに登録することがあります。</span><span class="sxs-lookup"><span data-stu-id="c9492-141">Your app or game engine may want to perform some processing right away or you may want to queue up the event data in your input processing routine.</span></span>

<span data-ttu-id="c9492-142">テンプレートには、開始するためのヘルパー クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c9492-142">The template includes a helper class to get you started.</span></span> <span data-ttu-id="c9492-143">このテンプレートは簡便設計の簡潔さを処理します。</span><span class="sxs-lookup"><span data-stu-id="c9492-143">This template forgoes any processing for simplicity of design.</span></span> <span data-ttu-id="c9492-144">ヘルパー クラスは 1 つかどうかの追跡以上**Pressed**最後のイベントが発生しました**Update**呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c9492-144">The helper class keeps track of whether one or more **Pressed** events occurred since the last **Update** call.</span></span> <span data-ttu-id="c9492-145">SpatialInputHandler.cpp: から</span><span class="sxs-lookup"><span data-stu-id="c9492-145">From SpatialInputHandler.cpp:</span></span>




```cpp
void SpatialInputHandler::OnSourcePressed(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    m_sourceState = args->State;
    
    //
    // TODO: In your app or game engine, rewrite this method to queue
    //       input events in your input class or event handler.
    //
}
```

<span data-ttu-id="c9492-146">そのため、返された場合、 [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)の次回の更新中に、最新の入力イベント。</span><span class="sxs-lookup"><span data-stu-id="c9492-146">If so, it returns the [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) for the most recent input event during the next Update.</span></span> <span data-ttu-id="c9492-147">SpatialInputHandler.cpp: から</span><span class="sxs-lookup"><span data-stu-id="c9492-147">From SpatialInputHandler.cpp:</span></span>




```cpp
// Checks if the user performed an input gesture since the last call to this method.
// Allows the main update loop to check for asynchronous changes to the user
// input state.
SpatialInteractionSourceState^ SpatialInputHandler::CheckForInput()
{
    SpatialInteractionSourceState^ sourceState = m_sourceState;
    m_sourceState = nullptr;
    return sourceState;
}
```

<span data-ttu-id="c9492-148">注すべて上記のコードで処理されるようになりますが、ユーザーがプライマリを実行するかどうか、同じ方法を押した**選択**キーを押すか、セカンダリ**メニュー**または**持ち**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c9492-148">Note that the code above will treat all presses the same way, whether the user is performing a primary **Select** press or a secondary **Menu** or **Grasp** press.</span></span> <span data-ttu-id="c9492-149">**選択**キーを押して、手、コント ローラーと音声、モーション コント ローラーではプライマリのトリガー/ボタンが押されたエア タップを実行する手動でいずれかをトリガーするモーションまたはユーザーの間でサポートされている操作の主なフォーム"Select"という音声します。</span><span class="sxs-lookup"><span data-stu-id="c9492-149">The **Select** press is a primary form of interaction supported across hands, motion controllers and voice, triggered either by a hand performing an air-tap, a motion controller with its primary trigger/button pressed, or the user's voice saying "Select".</span></span> <span data-ttu-id="c9492-150">選択操作が対象となるホログラムをアクティブ化するユーザーの意図を表します。</span><span class="sxs-lookup"><span data-stu-id="c9492-150">Select presses represent the user's intention to activate the hologram they are targeting.</span></span>

<span data-ttu-id="c9492-151">キーを押しての種類についての理由が発生している、SpatialInteractionManager::SourceUpdated イベント ハンドラーを変更します。</span><span class="sxs-lookup"><span data-stu-id="c9492-151">To reason about which kind of press is occurring, we will modify the SpatialInteractionManager::SourceUpdated event handler.</span></span> <span data-ttu-id="c9492-152">コードでは、(利用できる) 場合に理解の押下を検出し、それらを使用して、キューブの位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9492-152">Our code will detect Grasp presses (where available) and use them to reposition the cube.</span></span> <span data-ttu-id="c9492-153">理解が利用できない場合は、代わりに押したときの選択を使用します。</span><span class="sxs-lookup"><span data-stu-id="c9492-153">If Grasp is not available, we will use Select presses instead.</span></span>

<span data-ttu-id="c9492-154">SpatialInputHandler.h には、次のプライベート メンバー宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="c9492-154">Add the following private member declarations to SpatialInputHandler.h:</span></span> 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

<span data-ttu-id="c9492-155">SpatialInputHandler.cpp を開きます。</span><span class="sxs-lookup"><span data-stu-id="c9492-155">Open SpatialInputHandler.cpp.</span></span> <span data-ttu-id="c9492-156">コンス トラクターに次のイベントの登録を追加します。</span><span class="sxs-lookup"><span data-stu-id="c9492-156">Add the following event registration to the constructor:</span></span> 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

<span data-ttu-id="c9492-157">これは、イベント ハンドラーのコードです。</span><span class="sxs-lookup"><span data-stu-id="c9492-157">This is the event handler code.</span></span> <span data-ttu-id="c9492-158">入力ソースには、把握が発生する場合は、[次へ] の更新ループのポインターの姿勢に格納されています。</span><span class="sxs-lookup"><span data-stu-id="c9492-158">If the input source is experiencing a Grasp, the pointer pose will be stored for the next update loop.</span></span> <span data-ttu-id="c9492-159">それ以外の場合、これは確認選択キーを押して代わりにします。</span><span class="sxs-lookup"><span data-stu-id="c9492-159">Otherwise, it will check for a Select press instead.</span></span> <span data-ttu-id="c9492-160">SpatialInputHandler.cpp: から</span><span class="sxs-lookup"><span data-stu-id="c9492-160">From SpatialInputHandler.cpp:</span></span>




```cpp
void SpatialInputHandler::OnSourceUpdated(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    if (args->State->Source->IsGraspSupported)
    {
        if (args->State->IsGrasped)
        {
            m_sourceState = args->State;
        }
    }
    else
    {
        if (args->State->IsSelectPressed)
        {
            m_sourceState = args->State;
        }
    }
}
```

<span data-ttu-id="c9492-161">デストラクターでイベント ハンドラーの登録を解除してください。</span><span class="sxs-lookup"><span data-stu-id="c9492-161">Make sure to unregister the event handler in the destructor.</span></span> <span data-ttu-id="c9492-162">SpatialInputHandler.cpp: から</span><span class="sxs-lookup"><span data-stu-id="c9492-162">From SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

<span data-ttu-id="c9492-163">再コンパイルして再デプロイします。</span><span class="sxs-lookup"><span data-stu-id="c9492-163">Recompile, and then redeploy.</span></span> <span data-ttu-id="c9492-164">テンプレート プロジェクトは、位置、回転するキューブを変更する相互作用を理解を認識できるようになりましたにします。</span><span class="sxs-lookup"><span data-stu-id="c9492-164">Your template project should now be able to recognize Grasp interactions to reposition the spinning cube.</span></span>

<span data-ttu-id="c9492-165">SpatialInteractionSource API には、広範な機能を使用してコント ローラーがサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c9492-165">The SpatialInteractionSource API supports controllers with a wide range of capabilities.</span></span> <span data-ttu-id="c9492-166">上記の例では、それを使用する前に理解がサポートされているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="c9492-166">In the example shown above, we check to see if Grasp is supported before trying to use it.</span></span> <span data-ttu-id="c9492-167">SpatialInteractionSource、一般的なを超えて以下のオプション機能をサポートしている**選択**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c9492-167">The SpatialInteractionSource supports the following optional features beyond the common **Select** press:</span></span>
* <span data-ttu-id="c9492-168">**メニュー ボタンをクリックします。** IsMenuSupported プロパティを調べることによって、サポートを確認します。</span><span class="sxs-lookup"><span data-stu-id="c9492-168">**Menu button:** Check support by inspecting the IsMenuSupported property.</span></span> <span data-ttu-id="c9492-169">サポートされている場合は、確認、 [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)メニュー ボタンかどうかを検索するプロパティが押されました。</span><span class="sxs-lookup"><span data-stu-id="c9492-169">When supported, check the [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if the menu button is pressed.</span></span>
* <span data-ttu-id="c9492-170">**ボタンを理解するには。** IsGraspSupported プロパティを調べることによって、サポートを確認します。</span><span class="sxs-lookup"><span data-stu-id="c9492-170">**Grasp button:** Check support by inspecting the IsGraspSupported property.</span></span> <span data-ttu-id="c9492-171">サポートされている場合は、確認、 [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)プロパティを理解がアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="c9492-171">When supported, check the [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if grasp is activated.</span></span>

<span data-ttu-id="c9492-172">SpatialInteractionSource では、コント ローラーの追加機能を備えたコント ローラー プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="c9492-172">For controllers, the SpatialInteractionSource has a Controller property with additional capabilities.</span></span>
* <span data-ttu-id="c9492-173">**HasThumbstick:** True の場合、コント ローラーは、スティックが。</span><span class="sxs-lookup"><span data-stu-id="c9492-173">**HasThumbstick:** If true, the controller has a thumbstick.</span></span> <span data-ttu-id="c9492-174">検査、 [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties)スティックを取得する SpatialInteractionSourceState のプロパティ x と y 値 (ThumbstickX および ThumbstickY)、ほかの押された状態 (IsThumbstickPressed)。</span><span class="sxs-lookup"><span data-stu-id="c9492-174">Inspect the [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) property of the SpatialInteractionSourceState to acquire the thumbstick x and y values (ThumbstickX and ThumbstickY), as well as its pressed state (IsThumbstickPressed).</span></span>
* <span data-ttu-id="c9492-175">**HasTouchpad:** True の場合、コント ローラーがタッチパッドにします。</span><span class="sxs-lookup"><span data-stu-id="c9492-175">**HasTouchpad:** If true, the controller has a touchpad.</span></span> <span data-ttu-id="c9492-176">タッチパッドの取得を SpatialInteractionSourceState の ControllerProperties プロパティを検査する x および y 値 (TouchpadX および TouchpadY) と、ユーザーが (IsTouchpadTouched) パッドをタッチし、(ダウン タッチパッドを押して、場合を把握するにはIsTouchpadPressed)。</span><span class="sxs-lookup"><span data-stu-id="c9492-176">Inspect the ControllerProperties property of the SpatialInteractionSourceState to acquire the touchpad x and y values (TouchpadX and TouchpadY), and to know if the user is touching the pad (IsTouchpadTouched) and if they are pressing the touchpad down (IsTouchpadPressed).</span></span>
* <span data-ttu-id="c9492-177">**SimpleHapticsController:** コント ローラーの SimpleHapticsController API では、コント ローラーの haptics 機能を検査でき、ハプティクス フィードバックを制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="c9492-177">**SimpleHapticsController:** The SimpleHapticsController API for the controller allows you to inspect the haptics capabilities of the controller, and it also allows you to control haptic feedback.</span></span>

<span data-ttu-id="c9492-178">なおタッチパッドとスティック-1 から 1 の両方の軸を (下から上、および左右から) の範囲。</span><span class="sxs-lookup"><span data-stu-id="c9492-178">Note that the range for touchpad and thumbstick from -1 to 1 for both axes (from bottom to top, and from left to right).</span></span> <span data-ttu-id="c9492-179">SpatialInteractionSourceState::SelectPressedValue プロパティを使用してアクセスは、アナログのトリガーの範囲には、0 ~ 1 の範囲が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c9492-179">The range for the analog trigger, which is accessed using the SpatialInteractionSourceState::SelectPressedValue property, has a range of 0 to 1.</span></span> <span data-ttu-id="c9492-180">値を true に等しくなる IsSelectPressed と 1 つ関連付けますその他の値を false に等しくなる IsSelectPressed で相互に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="c9492-180">A value of 1 correlates with IsSelectPressed being equal to true; any other value correlates with IsSelectPressed being equal to false.</span></span>

<span data-ttu-id="c9492-181">ある手の形と、コント ローラーの両方でこれとは、コント ローラーのポインティング光線を表すポインター姿勢を異なる - SpatialInteractionSourceState::Properties::TryGetLocation を使用すると、ユーザーの手の形の位置が提供されますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c9492-181">Note that for both a hand and a controller, using SpatialInteractionSourceState::Properties::TryGetLocation will provide the user's hand position - this is distinct from the pointer pose representing the controller's pointing ray.</span></span> <span data-ttu-id="c9492-182">何かを手の形の位置に描画する場合は、TryGetLocation を使用します。</span><span class="sxs-lookup"><span data-stu-id="c9492-182">If you want to draw something at the hand location, use TryGetLocation.</span></span> <span data-ttu-id="c9492-183">コント ローラーの先端から raycast にする場合は、上、SpatialPointerPose TryGetInteractionSourcePose からポインティング射線を取得します。</span><span class="sxs-lookup"><span data-stu-id="c9492-183">If you want to raycast from the tip of the controller, get the pointing ray from TryGetInteractionSourcePose on the SpatialPointerPose.</span></span>

<span data-ttu-id="c9492-184">手入力するか、デバイスの表示または準備完了の位置 (インデックス指 palm フォワードと発生します) の内外での移動とのままにした場合、反応またはモーションと SpatialInteractionManager、SourceDetected SourceLost などの他のイベントを使用することもできます。コント ローラーは、オン/オフになってまたはペアになっているペアします。</span><span class="sxs-lookup"><span data-stu-id="c9492-184">You can also use the other events on SpatialInteractionManager, such as SourceDetected and SourceLost, to react when hands enter or leave the device's view or when they move in or out of the ready position (index finger raised with palm forward), or when motion controllers are turned on/off or are paired/unpaired.</span></span>

### <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="c9492-185">グリップの姿勢ポインティング ポーズとの比較</span><span class="sxs-lookup"><span data-stu-id="c9492-185">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="c9492-186">Windows Mixed Reality は、さまざまなフォーム ファクターでモーションのコント ローラーをサポートしている、各コント ローラーの設計と、ユーザーの手の形の位置とそのアプリの方向を「転送」自然の間の関係の違いポイントを表示するときに使用する必要があります、コント ローラー。</span><span class="sxs-lookup"><span data-stu-id="c9492-186">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="c9492-187">これらのコント ローラーをより適切に表すには、各操作のソースを調査することができますが発生 2 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="c9492-187">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>
* <span data-ttu-id="c9492-188">**グリップ姿勢**、片手で行うことによって、HoloLens、検出された手の形のまたはアニメーション コント ローラーを保持している片手で行うことのいずれかの場所を表します。</span><span class="sxs-lookup"><span data-stu-id="c9492-188">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="c9492-189">イマーシブ ヘッドセットは、この姿勢が最適な表示に使用**ユーザーの手**または**オブジェクトは、ユーザーの手の形で保持されている**剣やガンなど。</span><span class="sxs-lookup"><span data-stu-id="c9492-189">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="c9492-190">**位置を握って**:Palm 重心当然ながら、コント ローラーを保持しているときに、左または右中央にグリップ内の位置を調整します。</span><span class="sxs-lookup"><span data-stu-id="c9492-190">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="c9492-191">**向きの適切な軸を握って**:5 本の指フラットな姿勢を形成する完全に開くと、射線は、palm に通常 (順方向から左 palm、適切な palm から旧バージョンとの)</span><span class="sxs-lookup"><span data-stu-id="c9492-191">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="c9492-192">**向きの順方向軸を握って**:部分的に (場合と同様、コント ローラーを保持している) の手の閉じるときに、"forward"チューブを通じて非 thumb 指によって形成されるポイントの半径。</span><span class="sxs-lookup"><span data-stu-id="c9492-192">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="c9492-193">**軸の向きを握って**:右と前方参照の定義が含まれるアップ軸。</span><span class="sxs-lookup"><span data-stu-id="c9492-193">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="c9492-194">を通じてグリップ姿勢をアクセスできる[SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span><span class="sxs-lookup"><span data-stu-id="c9492-194">You can access the grip pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span></span>
* <span data-ttu-id="c9492-195">**ポインター姿勢**、フォワード指し示すコント ローラーのヒントを表します。</span><span class="sxs-lookup"><span data-stu-id="c9492-195">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="c9492-196">この姿勢が raycast に適してとき**UI をポイント**コント ローラー モデル自体をレンダリングする場合。</span><span class="sxs-lookup"><span data-stu-id="c9492-196">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="c9492-197">を通じてポインター姿勢をアクセスできる[SpatialInteractionSourceState.Properties.TryGetLocation(...) します。SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)または[SpatialInteractionSourceState.TryGetPointerPose(...) します。TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)します。</span><span class="sxs-lookup"><span data-stu-id="c9492-197">You can access the pointer pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...).SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) or [SpatialInteractionSourceState.TryGetPointerPose(...).TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span></span>

### <a name="composite-gestures-spatialgesturerecognizer"></a><span data-ttu-id="c9492-198">複合のジェスチャ。SpatialGestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="c9492-198">Composite gestures: SpatialGestureRecognizer</span></span>

<span data-ttu-id="c9492-199">A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)空間表面のジェスチャのイベントに手、アニメーション コント ローラー、および音声の選択 コマンドからユーザーの相互作用のヘッド視線の先を使用してユーザー対象を解釈します。</span><span class="sxs-lookup"><span data-stu-id="c9492-199">A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interprets user interactions from hands, motion controllers, and the "Select" voice command to surface spatial gesture events, which users target using their head gaze.</span></span>

<span data-ttu-id="c9492-200">空間ジェスチャとは、Windows Mixed Reality アプリ用の入力のキーの形式です。</span><span class="sxs-lookup"><span data-stu-id="c9492-200">Spatial gestures are a key form of input for Windows Mixed Reality apps.</span></span> <span data-ttu-id="c9492-201">ルーティングの相互作用によって、SpatialInteractionManager からホログラムの SpatialGestureRecognizer に、アプリ イベントを検出できますタップ、保持、操作、およびナビゲーション一様に手、音声、および空間の入力デバイス間での押下を処理する必要はありません。手動で解放します。</span><span class="sxs-lookup"><span data-stu-id="c9492-201">By routing interactions from the SpatialInteractionManager to a hologram's SpatialGestureRecognizer, apps can detect Tap, Hold, Manipulation, and Navigation events uniformly across hands, voice, and spatial input devices, without having to handle presses and releases manually.</span></span>

<span data-ttu-id="c9492-202">SpatialGestureRecognizer を要求するジェスチャ セットの間の最小限の曖昧のみを実行します。</span><span class="sxs-lookup"><span data-stu-id="c9492-202">SpatialGestureRecognizer performs only the minimal disambiguation between the set of gestures that you request.</span></span> <span data-ttu-id="c9492-203">たとえば、タップするだけを要求する場合ようおり、タップが引き続き発生を指がユーザーに押し可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c9492-203">For example, if you request just Tap, the user may hold their finger down as long as they like and a Tap will still occur.</span></span> <span data-ttu-id="c9492-204">要求した場合は、タップ押しすると、約 1 秒が指を保持しているのでは、ジェスチャは保留リストに昇格し、タップは行われなくとの両方。</span><span class="sxs-lookup"><span data-stu-id="c9492-204">If you request both Tap and Hold, after about a second of holding down their finger, the gesture will promote to a Hold and a Tap will no longer occur.</span></span>

<span data-ttu-id="c9492-205">SpatialGestureRecognizer を使用する処理 SpatialInteractionManager の[InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected)イベントと公開されている、SpatialPointerPose グラブします。</span><span class="sxs-lookup"><span data-stu-id="c9492-205">To use SpatialGestureRecognizer, handle the SpatialInteractionManager's [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) event and grab the SpatialPointerPose exposed there.</span></span> <span data-ttu-id="c9492-206">積集合を持つ、ホログラムこの姿勢からユーザーのヘッド注視光線を使用し、画面がユーザーの環境では、ユーザーのプログラムと対話するかを判断するためにメッシュします。</span><span class="sxs-lookup"><span data-stu-id="c9492-206">Use the user's head gaze ray from this pose to intersect with the holograms and surface meshes in the user's surroundings, in order to determine what the user is intending to interact with.</span></span> <span data-ttu-id="c9492-207">その後、ターゲット ホログラムの SpatialGestureRecognizer、イベント引数の中で、SpatialInteraction をルーティングを使用してその[CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction)メソッド。</span><span class="sxs-lookup"><span data-stu-id="c9492-207">Then, route the SpatialInteraction in the event arguments to the target hologram's SpatialGestureRecognizer, using its [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) method.</span></span> <span data-ttu-id="c9492-208">に従ってその相互作用の解釈が起動、 [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) - の作成時に、その認識エンジンで設定[TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)します。</span><span class="sxs-lookup"><span data-stu-id="c9492-208">This starts interpreting that interaction according to the [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) set on that recognizer at creation time - or by [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span></span>

<span data-ttu-id="c9492-209">HoloLens での相互作用とジェスチャ一般を派生させてください、ユーザーの視線入力ヘッドからターゲットではなくしようとしてレンダリングまたはして手のアイコンの場所に直接対話します。</span><span class="sxs-lookup"><span data-stu-id="c9492-209">On HoloLens, interactions and gestures should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="c9492-210">相互作用が開始されたら、操作やナビゲーションのジェスチャと同様、手の相対的な動きをジェスチャを制御を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c9492-210">Once an interaction has started, relative motions of the hand may be used to control the gesture, as with the Manipulation or Navigation gesture.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9492-211">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9492-211">See also</span></span>
* [<span data-ttu-id="c9492-212">視線入力</span><span class="sxs-lookup"><span data-stu-id="c9492-212">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="c9492-213">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="c9492-213">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="c9492-214">アニメーション コント ローラー</span><span class="sxs-lookup"><span data-stu-id="c9492-214">Motion controllers</span></span>](motion-controllers.md)
