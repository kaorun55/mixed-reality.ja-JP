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
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a>視線、ジェスチャ、および DirectX でモーション コント ローラー

プラットフォーム上に直接構築しようとしているなどを使用して、ユーザーを検索する場所のユーザーからの入力の受信を処理する必要があります[ヘッド注視](gaze.md)ユーザーがの選択と[ジェスチャ](gestures.md)または[コント ローラーのモーション](motion-controllers.md)します。 これらのフォームの入力を組み合わせると、配置するユーザーを有効ことができます、[ホログラム](hologram.md)アプリ。 [Holographic アプリ テンプレート](creating-a-holographic-directx-project.md)使いやすい例があります。

>[!NOTE]
>この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。  概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。

## <a name="gaze-input"></a>視線入力

ユーザーのアクセスに[ヘッド注視](gaze.md)を使用する、 [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx)型。 Holographic アプリ テンプレートには、視線の先についての基本的なコードが含まれています。 このコードにより、ユーザーの視点で、デバイスの位置と向きを考慮して書き込むフォワード ポイント ベクター、特定[座標系](coordinate-systems-in-directx.md)します。




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

なぜかを見つけることがあります。「しかし座標系はどこからでしょうか。」

質問にお答えしておきましょう。 AppMain の**Update**関数、StationaryFrameOfReference 用の座標系を基準と取得することによって空間の入力イベントを処理します。 設定するときに、StationaryFrameOfReference が作成されたことを思い出してください、 [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)、座標システムの起動時に取得され[Update](rendering-in-directx.md)します。




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

データはある種のポインターの状態に関連付けられていることに注意してください。 私たちは空間の入力イベントからこれを取得します。 イベント データ オブジェクトには、するため、必要な空間座標系を常に、イベントの時点で視線方向を関連付けることができます、座標系が含まれています。 実際には、これをポインター姿勢を取得するために行う必要があります。

> [!NOTE]
> HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。

## <a name="gesture-and-motion-controller-input"></a>ジェスチャとアニメーション コント ローラーの入力

Windows Mixed Reality でどちらも渡す[ジェスチャ](gestures.md)と[コント ローラーのモーション](motion-controllers.md)にある同じ空間入力 Api によって処理されます、 [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)名前空間。 などの一般的なアクションを簡単に処理できます**選択**ハンドとアニメーション コント ローラーの両方で同じ方法を押します。

複合現実でジェスチャやアニメーション コント ローラーを処理するときに対象にできます API の 2 つのレベルです。
* [相互作用](gestures.md#the-two-core-gestures-of-hololens)([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx)、 [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx)と[SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)) を使用してアクセスされる、 [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)
* [複合ジェスチャ](gestures.md#composite-gestures)([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx)、保持、操作、ナビゲーション) を使用してアクセスされる、 [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a>選択/メニュー/理解/タッチパッド/スティックの相互作用:SpatialInteractionManager

起動する手と Windows Mixed Reality で入力デバイスの間で低レベルの押下、リリースと更新プログラムを検出するために、 [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)します。 SpatialInteractionManager が手の形のときに、アプリに通知するイベントまたはアニメーション コント ローラーが入力を検出します。

SpatialInteractionSource の 3 のキーの種類は、それぞれ異なる SpatialInteractionSourceKind 値で表されます。
* **ハンド**検出されたユーザーの手の形を表します。 手動のソースは、HoloLens でのみ使用できます。
* **コント ローラー**ペアになっているアニメーション コント ローラーを表します。 モーションのコント ローラーは、たとえば、機能のさまざまなを提供できます。トリガー、メニュー ボタン、ボタンの把握、タッチパッドおよびサムスティックを選択します。
* **音声**システム検出キーワードを言うと、ユーザーの音声を表します。 キーを押して挿入され、ユーザーは、"Select"が話すたびにリリースされます。

押す間でこれらの操作のソースのいずれかを検出するには、SpatialInputHandler.cpp で SpatialInteractionManager で SourcePressed イベントを処理することができます。


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

押されたこのイベントは、アプリに非同期的に送信されます。 アプリやゲーム エンジンはすぐに、いくつか処理を実行することがあります。 またはルーチンを処理する、入力イベント データをキューに登録することがあります。

テンプレートには、開始するためのヘルパー クラスが含まれています。 このテンプレートは簡便設計の簡潔さを処理します。 ヘルパー クラスは 1 つかどうかの追跡以上**Pressed**最後のイベントが発生しました**Update**呼び出します。 SpatialInputHandler.cpp: から




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

そのため、返された場合、 [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)の次回の更新中に、最新の入力イベント。 SpatialInputHandler.cpp: から




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

注すべて上記のコードで処理されるようになりますが、ユーザーがプライマリを実行するかどうか、同じ方法を押した**選択**キーを押すか、セカンダリ**メニュー**または**持ち**キーを押します。 **選択**キーを押して、手、コント ローラーと音声、モーション コント ローラーではプライマリのトリガー/ボタンが押されたエア タップを実行する手動でいずれかをトリガーするモーションまたはユーザーの間でサポートされている操作の主なフォーム"Select"という音声します。 選択操作が対象となるホログラムをアクティブ化するユーザーの意図を表します。

キーを押しての種類についての理由が発生している、SpatialInteractionManager::SourceUpdated イベント ハンドラーを変更します。 コードでは、(利用できる) 場合に理解の押下を検出し、それらを使用して、キューブの位置を指定します。 理解が利用できない場合は、代わりに押したときの選択を使用します。

SpatialInputHandler.h には、次のプライベート メンバー宣言を追加します。 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

SpatialInputHandler.cpp を開きます。 コンス トラクターに次のイベントの登録を追加します。 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

これは、イベント ハンドラーのコードです。 入力ソースには、把握が発生する場合は、[次へ] の更新ループのポインターの姿勢に格納されています。 それ以外の場合、これは確認選択キーを押して代わりにします。 SpatialInputHandler.cpp: から




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

デストラクターでイベント ハンドラーの登録を解除してください。 SpatialInputHandler.cpp: から


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

再コンパイルして再デプロイします。 テンプレート プロジェクトは、位置、回転するキューブを変更する相互作用を理解を認識できるようになりましたにします。

SpatialInteractionSource API には、広範な機能を使用してコント ローラーがサポートしています。 上記の例では、それを使用する前に理解がサポートされているかどうかを確認します。 SpatialInteractionSource、一般的なを超えて以下のオプション機能をサポートしている**選択**キーを押します。
* **メニュー ボタンをクリックします。** IsMenuSupported プロパティを調べることによって、サポートを確認します。 サポートされている場合は、確認、 [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)メニュー ボタンかどうかを検索するプロパティが押されました。
* **ボタンを理解するには。** IsGraspSupported プロパティを調べることによって、サポートを確認します。 サポートされている場合は、確認、 [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)プロパティを理解がアクティブにします。

SpatialInteractionSource では、コント ローラーの追加機能を備えたコント ローラー プロパティがあります。
* **HasThumbstick:** True の場合、コント ローラーは、スティックが。 検査、 [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties)スティックを取得する SpatialInteractionSourceState のプロパティ x と y 値 (ThumbstickX および ThumbstickY)、ほかの押された状態 (IsThumbstickPressed)。
* **HasTouchpad:** True の場合、コント ローラーがタッチパッドにします。 タッチパッドの取得を SpatialInteractionSourceState の ControllerProperties プロパティを検査する x および y 値 (TouchpadX および TouchpadY) と、ユーザーが (IsTouchpadTouched) パッドをタッチし、(ダウン タッチパッドを押して、場合を把握するにはIsTouchpadPressed)。
* **SimpleHapticsController:** コント ローラーの SimpleHapticsController API では、コント ローラーの haptics 機能を検査でき、ハプティクス フィードバックを制御することもできます。

なおタッチパッドとスティック-1 から 1 の両方の軸を (下から上、および左右から) の範囲。 SpatialInteractionSourceState::SelectPressedValue プロパティを使用してアクセスは、アナログのトリガーの範囲には、0 ~ 1 の範囲が含まれています。 値を true に等しくなる IsSelectPressed と 1 つ関連付けますその他の値を false に等しくなる IsSelectPressed で相互に関連付けます。

ある手の形と、コント ローラーの両方でこれとは、コント ローラーのポインティング光線を表すポインター姿勢を異なる - SpatialInteractionSourceState::Properties::TryGetLocation を使用すると、ユーザーの手の形の位置が提供されますに注意してください。 何かを手の形の位置に描画する場合は、TryGetLocation を使用します。 コント ローラーの先端から raycast にする場合は、上、SpatialPointerPose TryGetInteractionSourcePose からポインティング射線を取得します。

手入力するか、デバイスの表示または準備完了の位置 (インデックス指 palm フォワードと発生します) の内外での移動とのままにした場合、反応またはモーションと SpatialInteractionManager、SourceDetected SourceLost などの他のイベントを使用することもできます。コント ローラーは、オン/オフになってまたはペアになっているペアします。

### <a name="grip-pose-vs-pointing-pose"></a>グリップの姿勢ポインティング ポーズとの比較

Windows Mixed Reality は、さまざまなフォーム ファクターでモーションのコント ローラーをサポートしている、各コント ローラーの設計と、ユーザーの手の形の位置とそのアプリの方向を「転送」自然の間の関係の違いポイントを表示するときに使用する必要があります、コント ローラー。

これらのコント ローラーをより適切に表すには、各操作のソースを調査することができますが発生 2 つの種類があります。
* **グリップ姿勢**、片手で行うことによって、HoloLens、検出された手の形のまたはアニメーション コント ローラーを保持している片手で行うことのいずれかの場所を表します。
    * イマーシブ ヘッドセットは、この姿勢が最適な表示に使用**ユーザーの手**または**オブジェクトは、ユーザーの手の形で保持されている**剣やガンなど。
    * **位置を握って**:Palm 重心当然ながら、コント ローラーを保持しているときに、左または右中央にグリップ内の位置を調整します。
    * **向きの適切な軸を握って**:5 本の指フラットな姿勢を形成する完全に開くと、射線は、palm に通常 (順方向から左 palm、適切な palm から旧バージョンとの)
    * **向きの順方向軸を握って**:部分的に (場合と同様、コント ローラーを保持している) の手の閉じるときに、"forward"チューブを通じて非 thumb 指によって形成されるポイントの半径。
    * **軸の向きを握って**:右と前方参照の定義が含まれるアップ軸。
    * を通じてグリップ姿勢をアクセスできる[SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).
* **ポインター姿勢**、フォワード指し示すコント ローラーのヒントを表します。
    * この姿勢が raycast に適してとき**UI をポイント**コント ローラー モデル自体をレンダリングする場合。
    * を通じてポインター姿勢をアクセスできる[SpatialInteractionSourceState.Properties.TryGetLocation(...) します。SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)または[SpatialInteractionSourceState.TryGetPointerPose(...) します。TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)します。

### <a name="composite-gestures-spatialgesturerecognizer"></a>複合のジェスチャ。SpatialGestureRecognizer

A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)空間表面のジェスチャのイベントに手、アニメーション コント ローラー、および音声の選択 コマンドからユーザーの相互作用のヘッド視線の先を使用してユーザー対象を解釈します。

空間ジェスチャとは、Windows Mixed Reality アプリ用の入力のキーの形式です。 ルーティングの相互作用によって、SpatialInteractionManager からホログラムの SpatialGestureRecognizer に、アプリ イベントを検出できますタップ、保持、操作、およびナビゲーション一様に手、音声、および空間の入力デバイス間での押下を処理する必要はありません。手動で解放します。

SpatialGestureRecognizer を要求するジェスチャ セットの間の最小限の曖昧のみを実行します。 たとえば、タップするだけを要求する場合ようおり、タップが引き続き発生を指がユーザーに押し可能性があります。 要求した場合は、タップ押しすると、約 1 秒が指を保持しているのでは、ジェスチャは保留リストに昇格し、タップは行われなくとの両方。

SpatialGestureRecognizer を使用する処理 SpatialInteractionManager の[InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected)イベントと公開されている、SpatialPointerPose グラブします。 積集合を持つ、ホログラムこの姿勢からユーザーのヘッド注視光線を使用し、画面がユーザーの環境では、ユーザーのプログラムと対話するかを判断するためにメッシュします。 その後、ターゲット ホログラムの SpatialGestureRecognizer、イベント引数の中で、SpatialInteraction をルーティングを使用してその[CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction)メソッド。 に従ってその相互作用の解釈が起動、 [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) - の作成時に、その認識エンジンで設定[TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)します。

HoloLens での相互作用とジェスチャ一般を派生させてください、ユーザーの視線入力ヘッドからターゲットではなくしようとしてレンダリングまたはして手のアイコンの場所に直接対話します。 相互作用が開始されたら、操作やナビゲーションのジェスチャと同様、手の相対的な動きをジェスチャを制御を使用できます。

## <a name="see-also"></a>関連項目
* [視線入力](gaze.md)
* [ジェスチャ](gestures.md)
* [アニメーション コント ローラー](motion-controllers.md)
