---
title: 手および DirectX でモーション コント ローラー
description: ネイティブの DirectX アプリで手の形の追跡およびモーションのコント ローラーを使用するための開発者ガイド。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: ハンド、アニメーション コント ローラー、directx、入力、ホログラム
ms.openlocfilehash: 08666c8c26cd4851c0c003a96a9e96d7a90228ac
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629645"
---
# <a name="hands-and-motion-controllers-in-directx"></a>手および DirectX でモーション コント ローラー

Windows Mixed Reality の両方を渡すと[モーションのコント ローラー](motion-controllers.md)で見つかった空間入力 Api を通じて入力を処理、 [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)名前空間。 などの一般的なアクションを簡単に処理できます**選択**ハンドとアニメーション コント ローラーの両方で同じ方法を押します。

## <a name="getting-started"></a>概要

Windows Mixed Reality で入力するアクセスの空間、するには、SpatialInteractionManager インターフェイスを起動します。  このインターフェイスを呼び出すことによってアクセスできる[SpatialInteractionManager::GetForCurrentView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview)、通常は、アプリの起動中のある時点からです。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

SpatialInteractionManager のジョブはへのアクセスを提供する[SpatialInteractionSources](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)入力のソースを表します。  SpatialInteractionSources の 3 つの種類は、システムで使用できます。
* **ハンド**検出されたユーザーの手の形を表します。 手動のソースは、HoloLens の基本的なジェスチャから追跡 HoloLens 2 をすべて連結したものの手に至るまで、デバイスに基づいてさまざまな機能を提供します。 
* **コント ローラー**ペアになっているアニメーション コント ローラーを表します。 アニメーション コント ローラーには、さまざまな機能を提供できます。  例:トリガー、メニュー ボタン、ボタンの把握、タッチパッドおよびサムスティックを選択します。
* **音声**システム検出キーワードを言うと、ユーザーの音声を表します。 たとえば、このソースは選択キーを押して挿入し、"Select"、ユーザーの質問されるたびにリリースします。

フレームごとのデータ ソースがによって表されるため、 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)インターフェイス。 アプリケーションで、イベント ドリブンまたはポーリング ベースのモデルを使用するかどうかに応じて、このデータにアクセスする 2 つのさまざまな方法はあります。

### <a name="event-driven-input"></a>イベント ドリブンの入力
SpatialInteractionManager では、アプリがリッスンできるイベント数を提供します。  例をいくつか含める[SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)、 [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)と[SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)します。

たとえば、次のコードは、MyApp::OnSourcePressed を呼び出して SourcePressed イベントをイベント ハンドラーをフックします。  これにより、相互作用のソースの任意の種類の押下を検出するために、アプリができます。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

押されたこのイベントは、押下の発生時に対応する SpatialInteractionSourceState と共に、非同期的に、アプリに送信されます。 アプリやゲーム エンジンはすぐに、いくつか処理を実行することがあります。 またはルーチンを処理する、入力イベント データをキューに登録することがあります。 [選択] ボタンが押されたかどうかを確認する方法を示しています、SourcePressed イベントのイベント ハンドラー関数を次に示します。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

デバイスのプライマリ アクションに対応する 'Select' を押してのみ、上記のコードをチェックします。 例には、HoloLens で、AirTap またはアニメーション コント ローラーに対してプルをトリガーが含まれます。  'Select' の押下では、対象とするホログラムをアクティブ化するユーザーの意図を表します。  SourcePressed イベントが多数のさまざまなボタンとジェスチャの発生し、そのような場合をテストする SpatialInteractionSource の他のプロパティを検査することができます。

### <a name="polling-based-input"></a>ポーリング ベースの入力
すべてのフレームの入力の現在の状態をポーリングするのに SpatialInteractionManager を使用することもできます。  これを行うには、単に呼び出す[GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp)すべてのフレーム。  この関数は、1 つを含む配列を返します[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)すべてアクティブ[SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)します。 つまり各モーションのアクティブなコント ローラーの各追跡対象の手および音声の 'select' コマンドが最近に載せた場合です。 アプリケーションにドライブの入力には、各 SpatialInteractionSourceState のプロパティを検査できます。 

ポーリング メソッドを使用して、'select' アクションを確認する方法の例を次に示します。 なお、*予測*変数を表します、 [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)オブジェクトから取得できますが、 [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

各 SpatialInteractionSource が、ID は、新しいソースを特定し、既存のソースのフレーム間を関連付けるために使用することができます。  コント ローラーの Id をセッションの期間にわたって静的なままのままにし、FOV を入力するたびに手には、新しい ID が割り当てられます。  SpatialInteractionManager 上など、イベントを使用できる[SourceDetected](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected)と[SourceLost](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)を手入力するか、デバイスのままにした場合、反応のビュー、またはアニメーション コント ローラーがオン/オフになっているかはペアになっていると対になっていません。

### <a name="predicted-vs-historical-poses"></a>履歴のポーズと予測
GetDetectedSourcesAtTimestamp がタイムスタンプ パラメーターを持つことに注意してください。 これにより、要求の状態を引き起こすのか、予測されたデータまたは入力の他のソースと空間的相互作用を関連付ける履歴、こと。 たとえば、現在のフレームに手の形の位置を表示するときに渡すことができますによって提供される予測のタイムスタンプで、 [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)します。 これにより、認識される待機時間を最小限に抑え、レンダリングされたフレームの出力に近づけるに手の形の位置を前方予測するシステムです。

ただし、このような予測の姿勢では、相互作用のソースと対象とするための理想的なポインティング射線は生成されません。 たとえば、アニメーション コント ローラーのボタンが押されたときに、オペレーティング システムに Bluetooth を通じてバブルアップするには、そのイベントの最大 20 ミリ秒かかることができます。 同様に、ユーザーが手のジェスチャを実行した後一定の時間はシステムに、ジェスチャと、アプリを検出し、それをポーリングする前に渡すことがあります。 状態変更のアプリのポーリング時間では、head と hand ポーズは相互作用が実際には、過去に発生したターゲットに使用されます。 GetDetectedSourcesAtTimestamp に現在 HolographicFrame のタイムスタンプを渡すことによって、対象とする場合、姿勢代わりにフォワード予測対象となるターゲット光線にフレームを表示する時に 20 ミリ秒以上を今後なることがあります。 今後この姿勢が適しています。*レンダリング*、相互作用ソースでは、時間の問題がそれにより*を対象とする*、対話ユーザーの対象とすると、過去に発生します。

さいわい、 [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)、 [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)と[SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)イベントは、履歴を提供[状態](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state)に関連付けられています。各入力イベント。  履歴ヘッドと hand ポーズがを通じて使用可能な直接が含まれます[TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)、履歴と共に[タイムスタンプ](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp)このイベントと関連付けるために他の Api に渡すことができます。

レンダリングおよび手とコント ローラーと各フレームを対象とする場合は、次のベスト プラクティスにつながります。
* **/コント ローラーの手の形のレンダリング**フレームごとに、アプリが**ポーリング**の**前方予測**現在のフレームの photon 時に各操作のソースの問題します。  呼び出すことによって相互作用のすべてのソースのポーリング[GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp)によって提供される予測のタイムスタンプを渡して、各フレーム[HolographicFrame::CurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.currentprediction)します。
* **手/コント ローラーを対象とする**押されたリリース時にキーを押してまたはリリースでは、アプリが処理する必要があります**イベント**、レイキャストがに基づいて、**履歴**ヘッドまたは手ポーズそのイベント。 処理することによってこのターゲットの射線を取得、 [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)または[SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)イベント、取得、[状態](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state)イベントの引数、およびそのを呼び出してからプロパティ[TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)メソッド。

## <a name="cross-device-input-properties"></a>デバイス間の入力プロパティ
SpatialInteractionSource API は、コント ローラーと追跡機能の広範なシステムの手をサポートします。 これらの機能の数は、デバイスの種類の間で共通です。 たとえば、手追跡とアニメーション コント ローラーの両方は、'select' アクションと 3D の位置を提供します。 可能な限り、API は、これらの一般的な機能を SpatialInteractionSource で同じプロパティにマップします。  これによりより簡単にさまざまな入力の種類をサポートするためにアプリケーションができます。 次の表に、サポートされているプロパティおよび入力の型の間で比較します。

| プロパティ | 説明 | HoloLens Gestures | アニメーション コント ローラー | 関節手|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**処理**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | 右側または左側にある/コント ローラー。 | サポートされない | サポート対象 | サポート対象 |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | 主ボタンの現在の状態。 | エア タップ | トリガー | 厳密でないエア タップ (垂直ピンチ) |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | グラブ ボタンの現在の状態。 | サポートされない | ボタンを取得します。 | ピンチまたは解決済みの手 |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | メニュー ボタンの現在の状態。    | サポートされない | メニュー ボタン | サポートされない |
| [SpatialInteractionSourceLocation::**位置**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | コント ローラーの手動またはグリップ位置の位置を XYZ します。 | Palm 場所 | グリップの姿勢位置 | Palm 場所 |
| [SpatialInteractionSourceLocation::**向き**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | コント ローラーの手動またはグリップ姿勢の方向を表す四元数。 | サポートされない | グリップの姿勢向き | Palm 向き |
| [SpatialPointerInteractionSourcePose::**位置**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | ポインティング射線の原点。 | サポートされない | サポート対象 | サポート対象 |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | ポインティング射線の方向です。 | サポートされない | サポート対象 | サポート対象 |

上記のプロパティの一部は、すべてのデバイスで使用できませんし、API がこれをテストするための手段を提供します。 たとえば、検査することができます、 [SpatialInteractionSource::IsGraspSupported](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported)プロパティ ソースが理解アクションを提供するかどうかを判断します。

### <a name="grip-pose-vs-pointing-pose"></a>グリップの姿勢ポインティング ポーズとの比較

Windows Mixed Reality は、さまざまなフォーム ファクターでモーションのコント ローラーをサポートします。  追跡システム関節手の形もサポートしています。  これらすべてのシステムは、手の形の位置とアプリがユーザーの手でポイントまたは rendreing オブジェクトを使用する自然な「前」方向の別のリレーションシップを持ちます。  このすべてをサポートするには、両方手の形の追跡、およびモーションのコント ローラーに指定された 3D ポーズの 2 つの種類があります。  最初は、ユーザーの手の形の位置を表すグリップ ポーズです。  2 つ目の姿勢で、ユーザーの手の形またはコント ローラーから送信されたポインティング光線を表しますが指しています。 したがって、表示する場合**ユーザーの手**または**オブジェクトは、ユーザーの手の形で保持されている**剣またはガン、グリップ姿勢を使用するなど、します。 コント ローラーまたは例では、ユーザーが手の形から raycast したい場合**UI でポイント**、ポインティングの姿勢を使用します。

アクセスできる、**グリップ姿勢**を通じて[SpatialInteractionSourceState::Properties::TryGetLocation(...)](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).次のように定義されます。
* **位置を握って**:Palm 重心当然ながら、コント ローラーを保持しているときに、左または右中央にグリップ内の位置を調整します。
* **向きの適切な軸を握って**:5 本の指フラットな姿勢を形成する完全に開くと、射線は、palm に通常 (順方向から左 palm、適切な palm から旧バージョンとの)
* **向きの順方向軸を握って**:部分的に (場合と同様、コント ローラーを保持している) の手の閉じるときに、"forward"チューブを通じて非 thumb 指によって形成されるポイントの半径。
* **軸の向きを握って**:右と前方参照の定義が含まれるアップ軸。

アクセスできる、**ポインター姿勢**を通じて[SpatialInteractionSourceState::Properties::TryGetLocation (...):: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)または[SpatialInteractionSourceState:。TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)します。

## <a name="controller-specific-input-properties"></a>コント ローラーに固有の入力プロパティ
SpatialInteractionSource では、コント ローラーの追加機能を備えたコント ローラー プロパティがあります。
* **HasThumbstick:** True の場合、コント ローラーは、スティックが。 検査、 [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties)スティックを取得する SpatialInteractionSourceState のプロパティ x と y 値 (ThumbstickX および ThumbstickY)、ほかの押された状態 (IsThumbstickPressed)。
* **HasTouchpad:** True の場合、コント ローラーがタッチパッドにします。 タッチパッドの取得を SpatialInteractionSourceState の ControllerProperties プロパティを検査する x および y 値 (TouchpadX および TouchpadY) と、ユーザーが (IsTouchpadTouched) パッドをタッチし、(ダウン タッチパッドを押して、場合を把握するにはIsTouchpadPressed)。
* **SimpleHapticsController:** コント ローラーの SimpleHapticsController API では、コント ローラーの haptics 機能を検査でき、ハプティクス フィードバックを制御することもできます。

タッチパッドとスティックの範囲が (下から上、および左から右へ) を両方の軸の 1 に-1 であることに注意してください。 SpatialInteractionSourceState::SelectPressedValue プロパティを使用してアクセスは、アナログのトリガーの範囲には、0 ~ 1 の範囲が含まれています。 値を true に等しくなる IsSelectPressed と 1 つ関連付けますその他の値を false に等しくなる IsSelectPressed で相互に関連付けます。

## <a name="articulated-hand-tracking"></a>追跡関節手
Windows Mixed Reality API では、追跡、たとえば HoloLens 2 で連結したものを完全にサポートを提供します。 追跡関節手の形は、アプリケーションで直接操作し、入力モデルをポイントし、コミットを実装するために使用できます。 完全カスタムのインタラクティビティの作成に使用できます。

### <a name="hand-skeleton"></a>手の形のスケルトン
追跡関節手の形では、により、さまざまな種類の相互作用の 25 の共通スケルトンを提供します。  スケルトンでは、インデックス/中間/リング/ほとんど本の指の 5 つの結合、つまみについては 4 つの結合および共同 1 手首を提供します。  手首ジョイントは、階層の基本として機能します。 次の図は、スケルトンのレイアウトを示しています。

![手の形のスケルトン](images/hand-skeleton.png)

ほとんどの場合、それが表すボーンに基づいて各ジョイントがという名前です。  すべての共同で 2 つのボーンがあるので、その位置に子ボーンに基づいて各ジョイント名前付け規則を使用します。  子ボーンは、ボーン手首からかけ離れたものとして定義されます。  たとえば、「インデックス位」共同が含まれています、インデックスの位ボーンの開始位置とそのボーンの方向。  ボーンの終了位置は含まれません。  必要がある場合はから取得して、[次へ]、階層、「インデックス中間」共同で結合。

25 の階層的な結合だけでなく、システムは、palm ジョイントを提供します。  片手で行うことはない通常の一部と見なさ骨組みです。  手の全体的な位置と向きを取得する便利な手段としてのみ提供されます。

次の情報は、共同の各提供されます。

| 名前 | 説明 |
|--- |--- |
|位置 | ジョイントは、要求されたすべての座標システムで使用できるの 3D の位置。 |
|方向 | すべてで利用可能、ボーンの 3D の方向は、座標系を要求します。 |
|半径 | 共同の位置にあるスキンの画面までの距離。 直接の対話、または本の指の幅に依存する視覚エフェクトをチューニングするために便利です。 |
|正確性 | この共同の情報について、システムの感覚を取ってにヒントを提供します。 |

関数を使用手の形のスケルトン データにアクセスすることができます、 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)します。  関数を呼び出す[TryGetHandPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)と呼ばれるオブジェクトを返すと[HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose)します。  ソースが思い起こさせます手をサポートしていない場合、この関数は null を返します。  呼び出して共同の現在のデータを取得するには、HandPose したら、 [TryGetJoint](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__)、関心がジョイントの名前に置き換えます。  として、データが返されます、 [JointPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.jointpose)構造体。  次のコードでは、人差し指先端の位置を取得します。 変数*currentState*のインスタンスを表します[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)します。

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>手の形メッシュ

API の追跡、連結したものを手動で完全に変形可能な三角形の手の形メッシュはできます。  このメッシュでは、手の形のスケルトンとリアルタイムで変形できるし、は高度な物理学の手法と同様に視覚エフェクトに便利です。  手の形メッシュにアクセスするには、最初に作成する必要があります、 [HandMeshObserver](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver)オブジェクトを呼び出すことによって[TryCreateHandMeshObserverAsync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)上、 [SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)します。  これは、1 回実行する、ソースあたり通常最初に表示するだけ済みます。  手の形に視界が入力したときに、HandMeshObserver オブジェクトを作成するには、この関数を呼び出しを意味します。  これは非同期関数では、ここでの同時実行の少し対処する必要がありますので注意してください。  利用可能になった HandMeshObserver オブジェクトを求める、三角形インデックス バッファーを呼び出して[GetTriangleIndices](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)します。  インデックスは、ソースの有効期間だけキャッシュし、1 回取得することができます、フレーム、経由でフレームを変更しないでください。  インデックスは、時計回りにワインディングの順序で提供されます。

次のコードでは、メッシュのオブザーバーを作成するデタッチ std::thread スピンアップし、メッシュ オブザーバーが使用可能、インデックス バッファーを抽出します。  という名前の変数から開始し*currentState*のインスタンスである[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)履歴手の形を表します。

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
非同期呼び出しを処理するための 1 つのオプションは、デタッチ スレッドを開始します。  またはを使って新しい[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)でサポートされる機能C++/WinRT です。

HandMeshObserver オブジェクトを作成したら、その対応する SpatialInteractionSource がアクティブになっている期間を保持する必要があります。  フレームごと、それを求める最新頂点バッファーを呼び出すことによって、手の形を表す[GetVertexStateForPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose)を渡して、 [HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose)頂点姿勢を表すインスタンス。  バッファー内の各頂点は、位置と標準があります。  手の形のメッシュの頂点の現在のセットを取得する方法の例を示します。  以前と同様、 *currentState*変数のインスタンスを表します[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)します。

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

スケルトンの結合とは異なり、手の形のメッシュ API はできません、頂点の座標システムを指定すること。  代わりに、 [HandMeshVertexState](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshvertexstate)座標システムで提供されている頂点を指定します。  呼び出してメッシュ変換を取得することができますし、 [TryGetTransformTo](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_)し、目的の座標系を指定します。  頂点を操作するたびに、このメッシュ変換を使用する必要があります。  このアプローチでは、レンダリングのために、メッシュを使用してのみ場合に特に、CPU オーバーヘッドが削減されます。

## <a name="gaze-and-commit-composite-gestures"></a>視線し、複合ジェスチャのコミット
HoloLens で特に注視し、コミットの入力モデルを使用するアプリケーションの (最初 gen) 空間の入力 API を提供、省略可能な[SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)上に構築された複合のジェスチャを有効にするには使用できる、' select' イベント。  ルーティングの相互作用によって、SpatialInteractionManager からホログラムの SpatialGestureRecognizer に、アプリ イベントを検出できますタップ、保持、操作、およびナビゲーション一様に手、音声、および空間の入力デバイス間での押下を処理する必要はありません。手動で解放します。

SpatialGestureRecognizer を要求するジェスチャ セットの間の最小限の曖昧のみを実行します。 たとえば、タップするだけを要求する場合ようおり、タップが引き続き発生を指がユーザーに押し可能性があります。 要求した場合は、タップ押しすると、約 1 秒が指を保持しているのでは、ジェスチャは保留リストに昇格し、タップは行われなくとの両方。

SpatialGestureRecognizer を使用する処理 SpatialInteractionManager の[InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected)イベントと公開されている、SpatialPointerPose グラブします。 積集合を持つ、ホログラムこの姿勢からユーザーのヘッド注視光線を使用し、画面がユーザーの環境では、ユーザーのプログラムと対話するかを判断するためにメッシュします。 その後、ターゲット ホログラムの SpatialGestureRecognizer、イベント引数の中で、SpatialInteraction をルーティングを使用してその[CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction)メソッド。 に従ってその相互作用の解釈が起動、 [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) - の作成時に、その認識エンジンで設定[TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)します。

HoloLens で (gen 最初) の相互作用とジェスチャのユーザーの視線入力ヘッドからターゲットではなくしようとしてレンダリングまたはして手のアイコンの場所に直接対話を派生する必要があります一般にします。 相互作用が開始されたら、操作やナビゲーションのジェスチャと同様、手の相対的な動きをジェスチャを制御を使用できます。

## <a name="see-also"></a>関連項目
* [DirectX で Head、目の視線入力](gaze-in-directx.md)
* [入力モデルを直接操作](direct-manipulation.md)
* [入力モデルをポイントし、コミット](point-and-commit.md)
* [入力モデルを注視とコミット](gaze-and-commit.md)
* [モーション コントローラー](motion-controllers.md)
